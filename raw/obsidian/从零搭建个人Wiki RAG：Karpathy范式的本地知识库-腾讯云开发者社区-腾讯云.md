---
title: "从零搭建个人Wiki RAG：Karpathy范式的本地知识库-腾讯云开发者社区-腾讯云"
source: "https://cloud.tencent.com/developer/article/2654881"
author:
published:
created: 2026-04-15
description: "本文介绍如何用LLM搭建个人Wiki知识库系统，无需向量数据库，300行代码实现离线RAG。通过Ollama本地模型编译Markdown笔记为结构化Wiki，支持高效检索和问答。提供完整实现方案，适合个人知识管理，数据完全自主可控。"
tags:
  - "clippings"
---
[社区首页](https://cloud.tencent.com/developer) > [专栏](https://cloud.tencent.com/developer/column) >从零搭建个人Wiki RAG：Karpathy范式的本地知识库

你有没有过这样的经历？

学了一堆技术，笔记散落在各处——有道云、飞书文档、VS Code的临时文件、浏览器的书签。想用的时候找不到，找到了又不记得上下文。

Karpathy（OpenAI联合创始人、前特斯拉AI总监）最近提出了一个优雅的解法： **LLM** **Wiki** ——不用 [向量数据库](https://cloud.tencent.com/product/vdb?from_column=20065&from=20065) ，不用传统RAG，让LLM自己维护一个Markdown知识库。

今天这篇文章，带你从零搭建一个 **可闭环的个人Wiki RAG系统** 。用Ollama本地模型，完全离线，代码不到300行。

读完你会觉得： **我行了，我也能搭。**

**Karpathy的LLM Wiki是什么？**

一句话： **让LLM帮你维护一个结构化的Markdown知识库。**

传统做法是这样的：

文档 → 分块 → Embedding → 向量 [数据库](https://cloud.tencent.com/product/tencentdb-catalog?from_column=20065&from=20065) → 检索 → LLM回答

Karpathy的做法是这样的：

raw笔记 → LLM编译 → 结构化Wiki → 直接塞给LLM

核心区别： **不需要向量数据库，不需要Embedding，不需要检索管线。** LLM读一个 `index.md` 全局索引，然后按需拉取具体的Wiki文章。

**优点：** 零基础设施，token效率高，人可读。

**缺点：** 知识量大了（超过100篇），一个context window装不下索引。

**我的方案：混合架构**

取两者之长：

raw/ → 原始知识素材（你的笔记） wiki/ → LLM编译后的结构化文章 向量索引 → 支持大规模精准检索

**Wiki层** 保证知识可读、可维护。 **RAG检索层** 保证知识量大了也能精准找到。

整个系统4个命令搞定：

wiki-rag compile # 编译raw → wiki wiki-rag query "你的问题" # 查询 wiki-rag add "主题" "内容" # 添加新知识 wiki-rag compile --force # 强制重新编译

**环境准备**

**▪ 1. 安装Ollama**

\# macOS brew install ollama ollama serve

**▪ 2. 拉取模型**

ollama pull deepseek-r1:1.5b # LLM（编译+回答） ollama pull nomic-embed-text # Embedding模型

为什么选这两个？ **轻量、离线、够用。** 1.5B模型在MacBook上秒回，nomic-embed-text是Ollama生态最常用的Embedding模型。

**▪ 3. 创建项目**

mkdir wiki-rag && cd wiki-rag

创建 `pyproject.toml` ：

\[project\] name = "wiki-rag" version = "0.1.0" requires-python = ">=3.10" dependencies = \[ "llama-index>=0.12.0", "numpy", \]

uv sync

**三层架构设计**

**▪ 第一层：raw/（原始素材）**

放你的笔记，随便写，Markdown格式：

raw/ ├── python-decorators.md ├── docker-network.md ├── git-rebase-merge.md ├── redis-data-structures.md └── http2-vs-http1.md

**▪ 第二层：wiki/（LLM编译后的结构化文章）**

LLM把你的乱七八糟笔记编译成结构化的Wiki文章：

COMPILE\_PROMPT = """你是一个知识整理专家。请将以下原始笔记编译为一篇结构清晰的Wiki文章。 要求： 1. 保留所有核心技术要点 2. 使用清晰的标题层级 3. 关键术语加粗 4. 保留核心代码 5. 末尾添加「一句话总结」 6. 生成3-5个标签"""

**智能跳过：** 用MD5哈希检测文件变化，没改动的自动跳过。

**▪ 第三层：向量索引（RAG检索）**

把Wiki文章分块，生成Embedding，存到本地JSON：

\# 分块 → Embedding → 存储 paragraphs = \[p for p in content.split("\\n\\n") if p.strip()\] for para in paragraphs: emb = client.embeddings(model="nomic-embed-text", prompt=para) chunks.append({"text": para, "embedding": emb\["embedding"\]})

查询时：问题Embedding → 余弦相似度 → 取Top3 → 拼接上下文 → LLM回答。

**核心代码**

整个系统就一个文件 `src/wiki_rag.py` ，不到300行。

**▪ 编译：raw → wiki**

def compile\_raw\_to\_wiki(raw\_file, force=False): # 1. 检查是否需要重新编译（MD5哈希） if not force and file\_hash\_unchanged(raw\_file): return None # 跳过 # 2. 调用LLM编译 content = raw\_file.read\_text() resp = client.chat(model="deepseek-r1:1.5b", messages=\[ {"role": "user", "content": COMPILE\_PROMPT.format(content=content)} \]) # 3. 写入wiki/ wiki\_path = WIKI\_DIR / raw\_file.name wiki\_path.write\_text(resp\["message"\]\["content"\])

**▪ 查询：向量检索 + LLM回答**

def query(question): # 1. 问题的Embedding q\_emb = client.embeddings(model="nomic-embed-text", prompt=question) # 2. 余弦相似度检索Top3 scored = \[(cosine\_sim(q\_emb, chunk\["embedding"\]), chunk) for chunk in index\_data\["chunks"\]\] top3 = sorted(scored, reverse=True)\[:3\] # 3. 拼接上下文 → LLM回答 context = "\\n\\n".join(chunk\["text"\] for \_, chunk in top3) resp = client.chat(model="deepseek-r1:1.5b", messages=\[ {"role": "user", "content": f"基于以下内容回答：\\n{context}\\n\\n问题：{question}"} \]) return resp\["message"\]\["content"\]

**就这么简单。** 没有向量数据库，没有FAISS，没有复杂的检索管线。

**跑起来**

\# 编译 uv run python -m src.wiki\_rag compile # 📝 编译: docker-network.md... ✅ 完成 # 📝 编译: redis-data-structures.md... ✅ 完成 #... # 📊 编译完成: 5 篇新编译 # 📑 索引已更新: 5 篇文章 # ✅ 向量索引构建完成: 68 个chunk # 查询 uv run python -m src.wiki\_rag query "Python装饰器是什么" # 💡 回答: Python装饰器是一种高阶函数...

**踩坑记录**

**▪ 坑1：LlamaIndex的Ollama集成502**

LlamaIndex的Ollama客户端在Mac上频繁502。

**解决方案：** 直接用 `ollama` Python SDK，绕过LlamaIndex的集成层。

**▪ 坑2：Ollama并发限制**

Embedding请求并发太高会502。

**解决方案：** 逐个请求，不批量。

**▪ 坑3：模型选择**

9B的Qwen模型编译5篇文章就要几分钟，还经常超时。

**解决方案：** 用1.5B的deepseek-r1，够快够用。

**扩展方向**

这个MVP能跑起来后，可以往这些方向扩展：

- **换更强的模型：** 等Mac内存够大，换7B/14B模型，编译质量会更好
- **换向量存储：** JSON → FAISS → Chroma，支持万级文档
- **增量更新：** 只重新编译变化的文件（已支持）
- **Web界面：** 加个Streamlit前端，从CLI变成Web应用
- **多源接入：** 不仅读Markdown，还能读PDF、网页、Notion

**完整代码**

**GitHub** **仓库：** https://github.com/helloworldtang/wiki-rag

clone下来，装好Ollama， `uv sync` + `compile` 就能跑。

**13个** **单元测试** **全通过，端到端验证成功。**

![](https://developer.qcloudimg.com/http-save/yehe-1126566/0804d568ffad2741364d6a2d32681c6e.png)

不是demo，是真能用的MVP。

![](https://developer.qcloudimg.com/http-save/yehe-1126566/4dc0838a516e787d9c79a8ea0fd7f964.png)

![](https://developer.qcloudimg.com/http-save/yehe-1126566/ee0d2014838d8063247f3dafce2435ad.png)

**一句话总结**

Karpathy说：知识管理正在成为AI工作流的核心成本。用LLM Wiki + RAG，你可以在本地搭建一个 **真正可用的个人知识库** ——零API费用，完全离线，数据自己掌控。

**试试看，你会发现：真没那么难。**

本文参与 [腾讯云自媒体同步曝光计划](https://cloud.tencent.com/developer/support-plan) ，分享自微信公众号。

原始发表：2026-04-10，如有侵权请联系 [cloudcommunity@tencent.com](mailto:cloudcommunity@tencent.com) 删除

本文分享自 的数字化之路 微信公众号，前往查看

如有侵权，请联系 [cloudcommunity@tencent.com](mailto:cloudcommunity@tencent.com) 删除。

本文参与 [腾讯云自媒体同步曝光计划](https://cloud.tencent.com/developer/support-plan) ，欢迎热爱写作的你一起参与！

[烟雨平生](https://cloud.tencent.com/developer/user/1126566) 0

LV.1

这个人很懒，什么都没有留下～

[

文章

247

](https://cloud.tencent.com/developer/user/1126566/articles)[

获赞

371

](https://cloud.tencent.com/developer/user/1126566)

专栏

2

交个朋友

加入腾讯云官网粉丝站

蹲全网底价单品 享第一手活动信息

![](https://cs.cloud.tencent.com/group1/M00/2E/70/C6E9n2gN0X-ACMf9AAAeCb2HQQE475.png)

相关产品与服务

数据库

云数据库为企业提供了完善的关系型数据库、非关系型数据库、分析型数据库和数据库生态工具。您可以通过产品选择和组合搭建，轻松实现高可靠、高可用性、高性能等数据库需求。云数据库服务也可大幅减少您的运维工作量，更专注于业务发展，让企业一站式享受数据上云及分布式架构的技术红利！

[产品介绍](https://cloud.tencent.com/product/tencentdb-catalog?from=21341&from_column=21341)

[2026采购季 | AI焕新·智启新局](https://cloud.tencent.com/act/pro/featured-202604?from=21344&from_column=21344)

相关课程

[一站式学习中心 >](https://cloud.tencent.com/developer/learning)