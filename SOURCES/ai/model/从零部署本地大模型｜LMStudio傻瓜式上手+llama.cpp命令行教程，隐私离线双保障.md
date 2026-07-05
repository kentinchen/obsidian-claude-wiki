---
title: "从零部署本地大模型｜LMStudio傻瓜式上手+llama.cpp命令行教程，隐私离线双保障"
source: "https://zhuanlan.zhihu.com/p/2016201481326440841"
author:
  - "[[月色清绝]]"
published:
created: 2026-06-28
description: "写在前面：现在很多人想用大模型，但又怕数据上传云端泄露（比如办公文档、敏感信息），要么觉得云端API长期订阅太贵，要么需要离线环境使用——本地部署就是最优解。 本文不搞虚的，全程保姆级，不管你是电脑小白…"
tags:
  - "clippings"
---
24 人赞同了该文章

目录

收起

一、先搞懂：为什么要本地部署大模型？

二、前置准备：硬件要求（重中之重，别买错、别踩坑）

三、模型下载

具体下载步骤

四、LMStudio图形化部署（傻瓜式一键搞定）

具体部署步骤

openclaw接入步骤

Claude Code 接入步骤

五、进阶选择：llama.cpp命令行部署（轻量高效，自定义性强）

具体部署步骤（以Windows系统为例，Mac/Linux类似）

六、常见问题FAQ（新手必看，解决90%的问题）

写在前面：现在很多人想用大模型，但又怕数据上传云端泄露（比如办公文档、敏感信息），要么觉得云端API长期订阅太贵，要么需要离线环境使用——本地部署就是最优解。  
本文不搞虚的，全程保姆级，不管你是电脑小白还是有点技术基础，都能跟着走。重点讲两种部署方式： [LMStudio](https://zhida.zhihu.com/search?content_id=271468771&content_type=Article&match_order=1&q=LMStudio&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4MTI0MjksInEiOiJMTVN0dWRpbyIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTQ2ODc3MSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.Z6JGYGCt8Wytbl4-ggLM3NugQSwhYm-_v7gdqeZamKE&zhida_source=entity) 图形化界面（傻瓜式一键搞定，新手首选）和llama.cpp命令行（轻量高效，进阶必学），再把硬件要求、模型选择这些坑提前踩平，帮你少走90%的弯路。

## 一、先搞懂：为什么要本地部署大模型？

核心就3个需求，戳中大多数人的痛点：

- **数据隐私绝对安全** ：所有对话、输入的内容都存在自己电脑里，不上传任何云端服务器，适合处理办公机密、个人隐私、敏感数据，再也不用怕数据泄露风险。
- **完全离线可用** ：部署完成后，断网也能正常使用，出差、野外、无网络环境下，依旧能调用大模型完成文案、翻译、代码辅助等工作。
- **长期使用成本极低** ：一次性下载模型，后续使用不花一分钱，比每月订阅云端API（比如 [GPT-4](https://zhida.zhihu.com/search?content_id=271468771&content_type=Article&match_order=1&q=GPT-4&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4MTI0MjksInEiOiJHUFQtNCIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTQ2ODc3MSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0._b38oLABO4hQqqiiBNwi658tSTKb4_7_T6CNAwcbh7g&zhida_source=entity) 、KimiK2.5）省不少钱，尤其适合高频使用人群。

一句话总结：本地部署 = 隐私自由 + 离线自由 + 省钱自由，新手也能轻松拿捏。

## 二、前置准备：硬件要求（重中之重，别买错、别踩坑）

大模型对硬件有要求，但不是非得顶配显卡，关键看你想部署的模型参数量和量化精度——参数量越小、量化精度越低，对硬件要求越低，反之则越高。先给大家讲清楚核心逻辑，再给具体配置建议，避免盲目跟风升级硬件。  
**核心原则**  
大模型运行的核心瓶颈是 **GPU显存（VRAM）** ，其次是CPU和内存；如果没有GPU，用CPU也能推理，但速度会慢10-50倍（具体看模型大小），日常应急可用，高频使用不推荐。  
具体配置建议（按模型规模分类，新手直接对号入座）

| 模型规模（参数量） | 推荐量化精度 | 显存需求 | 推荐GPU | CPU/内存最低要求 | 适用场景 |
| --- | --- | --- | --- | --- | --- |
| 7B（新手首选） | Q4\_K\_M（兼顾速度和效果） | ~4GB | RTX 3060/4060（12GB显存） | CPU：四核8线程；内存：16GB | 日常对话、文案生成、简单代码辅助 |
| 13B（进阶选择） | Q4\_K\_M/Q5\_K\_M | ~8GB | RTX 3080/4080（16GB+显存） | CPU：八核16线程；内存：32GB | 复杂对话、专业领域问答、代码调试 |
| 70B（高阶需求） | Q4\_K\_M | ~40GB | A100 80G/4×A10 | CPU：十六核32线程；内存：64GB+ | 企业级应用、深度科研、复杂推理 |

> 避坑提醒：① 不要盲目追求大参数量，7B量化版足够大多数人日常使用，13B以上对硬件要求陡增，新手慎选；② 显存一定要比模型量化后需求大1-2GB，避免加载失败；③ 存储建议用NVMe SSD，模型加载速度会快很多，普通机械硬盘会卡顿。

## 三、模型下载

本地部署的核心是“模型文件”，相当于大模型的“大脑”，我们优先选择国内的魔塔社区（ModelScope）下载——不用科学上网，模型资源丰富，还能根据自己的硬件条件筛选，对国内用户极其友好。

### 具体下载步骤

1. 打开魔塔社区官网： [ModelScope 魔搭社区](https://link.zhihu.com/?target=https%3A//www.modelscope.cn/home) （无需注册也能下载，注册后可享受更快下载速度）。
2. 搜索模型：在首页搜索框输入你想下载的模型（新手推荐优先选这些：Qwen3.5-9B、 [Llama3.1-8B](https://zhida.zhihu.com/search?content_id=271468771&content_type=Article&match_order=1&q=Llama3.1-8B&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4MTI0MjksInEiOiJMbGFtYTMuMS04QiIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTQ2ODc3MSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.P4yfDJtO_KKgYHbDya67LBZHcln6k3fT9UH7UZxCFAs&zhida_source=entity) 、DeepSeek-R1-8B，中文支持好、资源占用适中）。下面我以Qwen3.5-9B-GGUF为例。

不同用途选择对应模型，能大幅提升使用体验，以下均为GGUF格式、7B/8B级参数量（适配普通硬件），可直接在魔塔社区搜索下载：  
1\. 专门用于聊天对话的模型（日常唠嗑、情感交流、通用问答）

- Qwen2.5-Chat-7B：中文支持极佳，对话自然流畅，共情能力强，适合日常聊天、生活问答、文案润色，量化版体积小，普通电脑可轻松加载。
- Llama3.1-Chat-8B：国际主流聊天模型，对话逻辑清晰，响应速度快，支持多轮长对话，适合需要严谨对话、多场景交互的需求。
- DeepSeek-Chat-7B：轻量化聊天模型，占用资源少，离线响应快，适合低配电脑，日常聊天、简单问答完全够用。

2\. 专门用于代码任务的模型（代码生成、调试、解释、重构）

- CodeLlama-7B-Chat：Meta官方推出的代码专用模型，支持Python、Java、C++等多种编程语言，能生成完整代码片段、调试报错、解释代码逻辑，适合编程新手和进阶开发者。
- DeepSeek-Coder-V2-7B：中文代码支持优秀，能适配国内开发者习惯，生成的代码简洁规范，支持代码补全、重构、注释生成，离线使用不依赖云端代码库。
- StarCoderBase-7B：开源免费，支持多语言代码，兼容性强，适合批量生成代码、简单脚本开发，搭配llama.cpp部署，推理速度快。

提示：筛选时直接搜索模型名称+“GGUF”，即可快速找到对应格式的量化版本，根据自己的硬件选择Q4\_K\_M（优先）或Q2\_K版本。

3\. 筛选模型：点击进入模型详情页，重点看“模型文件”部分，根据自己的硬件选择 **量化版本，** 同时优先选择GGUF格式（原因下文补充）

1. 新手首选Q4\_K\_M版本：压缩比适中，精度损失小，对硬件要求低；
	2. 追求精度选Q8\_0版本：近乎无损，和原生模型差距不大，但需要更多显存；
	3. 硬件较差选Q2\_K版本：体积最小，但精度损失较明显，仅适合应急。
![](https://pic2.zhimg.com/v2-72896323ac48ebe3b73ba807fa729d37_1440w.jpg)

4\. 下载模型：点击模型文件后的“下载”按钮，下载后保存到容易找到的文件夹（比如D盘“LLM模型”文件夹），记住路径，后续部署会用到。

![](https://pic4.zhimg.com/v2-78174513411e644e2f70b2225fdc6fff_1440w.jpg)

> 避坑提醒：① 下载时注意模型格式，LMStudio和llama.cpp优先支持GGUF格式，别下载错成其他格式（比如PyTorch格式），否则无法加载；② 模型文件较大（7B量化版约3-5GB），建议在网络稳定时下载，避免重复耗时。

**为什么优先选择GGUF格式？**  
GGUF是目前本地大模型部署的“最优格式”，尤其适配LMStudio和llama.cpp，核心原因有4点，贴合本地部署的核心需求：

- 轻量高效，适配本地硬件：GGUF格式支持多种量化精度（Q2\_K、Q4\_K\_M、Q8\_0等），能在大幅压缩模型体积的同时，尽量保留模型性能，完美适配普通电脑的CPU/GPU显存，避免因模型体积过大导致加载失败。
- 跨平台兼容性强：无论是Windows、Mac（Apple Silicon芯片）还是Linux系统，GGUF格式都能无缝适配LMStudio、llama.cpp等主流本地部署工具，不用额外转换格式，下载后可直接加载使用，小白友好。
- 推理速度更快：GGUF格式针对本地推理做了专门优化，能更好地调用CPU/GPU资源，相比其他格式（如PyTorch的.bin格式），推理速度提升10%-30%，尤其适合CPU推理场景。
- 生态完善，支持广泛：目前主流的本地部署工具（LMStudio、llama.cpp、Oobabooga等）都将GGUF作为默认支持格式，魔塔社区等国内平台也已收录大量GGUF格式模型，下载和使用更便捷，无需额外配置。

## 四、LMStudio图形化部署（傻瓜式一键搞定）

如果你是电脑小白，不想搞复杂的命令行，LMStudio绝对是你的福音——一款专门用于本地大模型部署的图形化工具，跨平台支持Windows、Mac、Linux，无需配置环境，一键加载模型，全程鼠标操作，5分钟就能搞定部署。  
LMStudio核心优势

- 开箱即用：内置所有依赖环境，安装后直接打开就能用，不用装Python、CUDA等复杂组件；
- 图形化操作：所有设置都有可视化界面，加载模型、调整参数、对话测试，全程鼠标点一点；
- 支持OpenAI API兼容：可以启动本地推理服务，对接其他AI工具（比如Openclaw），实用性拉满；
- 硬件自动优化：会自动识别你的CPU/GPU，开启CUDA加速、Flash Attention等优化，最大化提升推理速度。

### 具体部署步骤

1. 下载LMStudio：打开官网（ [lmstudio.ai/](https://link.zhihu.com/?target=https%3A//lmstudio.ai/) ），根据自己的系统（Windows/Mac/Linux）下载对应安装包，大小约100MB，下载速度很快。
![](https://pic1.zhimg.com/v2-2f6216d9950ec250efe2054f9d14c0d4_1440w.jpg)

2\. 安装LMStudio：双击安装包，一路下一步即可（建议安装到非系统盘，比如D盘，避免占用C盘空间），安装完成后打开软件，无需注册，直接进入主界面。

![](https://pica.zhimg.com/v2-45b13103c6fa01621146b6e7ad8447c4_1440w.jpg)

![](https://picx.zhimg.com/v2-039b16d083606e1650fff099fedb8e3b_1440w.jpg)

![](https://pica.zhimg.com/v2-bb031ee091b82d6b74ad1dd55ab82e9a_1440w.jpg)

3\. 加载本地模型：

1. 打开LMStudio后，再点击右上角下载按钮，然后打开下载文件夹；
	2. 找到之前从魔塔社区下载的模型文件夹，选中模型文件（GGUF格式，后缀为.gguf），复制到下载文件夹。
![](https://picx.zhimg.com/v2-d79a3659e7a4af41520653704b755fb5_1440w.jpg)

复制到下载文件夹，这里LMStudio默认的下载文件夹就是放在C盘路径下的，并且无法更改。

![](https://pic3.zhimg.com/v2-da107eda2ed1380e5df812396a7eed5a_1440w.jpg)

点击MyModel，可以看到已经被识别，如果只需要聊天，点击Use In New Chat即可，如果需要使用到API还需要加载模型，详细步骤看下面。

![](https://pica.zhimg.com/v2-695b2a0cc78b07a5766e4a8f34f40e6a_1440w.jpg)

4\. 调整推理参数（可选，新手默认即可）：

1. 加载完成后，点击左侧“Settings”，可以调整参数优化体验：
	2. Temperature（温度）：默认0.7，数值越低，回答越严谨；数值越高，回答越有创意；
	3. Max Context Length（上下文长度）：默认2048，数值越大，能记住的对话内容越多，但越占用硬件资源,也就是回复的速度越慢；
	4. Hardware Acceleration（硬件加速）：默认开启，会自动识别GPU，优先选择“CUDA”（NVIDIA显卡）或“Metal”（Mac芯片），开启后推理速度会大幅提升。

5\. 开始使用：点击左侧“Chat”，输入问题，就能和本地大模型对话了！断网测试一下，完全可以正常使用，所有对话数据都存在本地，隐私拉满。

![](https://picx.zhimg.com/v2-b6774281cdf1ee55b5e8421616dacd3f_1440w.jpg)

> 实用技巧：① 如果加载模型失败，大概率是模型格式不对（不是GGUF）或显存不足，换个小参数量、低量化版本的模型即可；② NVIDIA显卡用户，确保安装了最新的CUDA驱动，能解锁更高推理速度，实测RTX 3080运行7B Q4\_K\_M模型，开启优化后推理速度可达每秒20+ tokens。

6\. 如果需要使用到API调用，比如openclaw、claudecode接入本地模型API，还需要加载模型，下面分别演示OpenClaw和 [ClaudeCode](https://zhida.zhihu.com/search?content_id=271468771&content_type=Article&match_order=1&q=ClaudeCode&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4MTI0MjksInEiOiJDbGF1ZGVDb2RlIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6MjcxNDY4NzcxLCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.eZsCEOeHzoSlFg1U0oxi6pv5bAhMS0jLwHCnu49-x18&zhida_source=entity) 接入本地模型API过程

![](https://pic1.zhimg.com/v2-4f82e265958c0360d7b0d7558c985fe0_1440w.jpg)

### openclaw接入步骤

1. 打开OpenClaw网关服务
```
# 打开Windows PowerShell，输入下面代码
openclaw gateway
```
![](https://pic4.zhimg.com/v2-9e657bb89c0aff1271c6b84c383dd367_1440w.jpg)

2\. 运行 `openclaw config`, 打开配置选项，选择Loacl后回车即可

![](https://picx.zhimg.com/v2-9fcdf8c34396f85adf27c4cd1698adaf_1440w.jpg)

3\. 选择模型

![](https://picx.zhimg.com/v2-f9050403749ad6667362a7b7009b1461_1440w.jpg)

4\. 按下方向箭头移动到最下面，选择Custom Provider

![](https://pic2.zhimg.com/v2-81a3a6a5e41aedc7ae0dfb48cd13b155_1440w.jpg)

5\. 输入配置，这里只需要输入三项，其余默认即可，API Base URL只需要修改端口号为1234，API Key随便输入因为本地不会校验Key，但是不输入又可能报错，最后输入模型ID。

![](https://pic4.zhimg.com/v2-fc993c11b3f8957e1e1dd5e8f37c9a17_1440w.jpg)

6\. 然后选择Continue即可

![](https://picx.zhimg.com/v2-e1292a74d2dc3658d1e05d7abe78dc89_1440w.jpg)

### Claude Code 接入步骤

下面我使用vscode用来演示

1. 在扩展中搜索Claude Code for VS Code然后安装
![](https://pic3.zhimg.com/v2-ff38dec54f68288ca01d1a953b6ac2ce_1440w.jpg)

2\. 安装完成后点击设置

![](https://pic2.zhimg.com/v2-ae7cc0c55e06a824b349945c7d3525a9_1440w.jpg)

3\. 点击编辑设置配置

![](https://pic3.zhimg.com/v2-a91ab75905bc5658ae9fe8360bd35f78_1440w.jpg)

4\. 复制下述代码到里面

```json
{
    "explorer.confirmDelete": false,
    "extensions.ignoreRecommendations": true,
    "security.workspace.trust.untrustedFiles": "open",
    "python.createEnvironment.trigger": "off",
    "claudeCode.allowDangerouslySkipPermissions": true,
    "claudeCode.environmentVariables": [
    
        {
            "name": "ANTHROPIC_BASE_URL",
            "value": "http://127.0.0.1:1234" // 指向LM Studio的本地Anthropic兼容地址
        },
        {
            "name": "ANTHROPIC_AUTH_TOKEN",
            "value": "1234" // 任意非空字符串，仅占位
        }
    ],
    "permissions": {
        "defaultMode": "bypassPermissions"
    },
    // 可选：强制插件使用本地模型，避免走官方接口
    "claudeCode.model": "qwen3.5-9b",
    "claudeCode.maxTokens": 20000,
    "claudeCode.preferredLocation": "panel"
}
```
![](https://picx.zhimg.com/v2-122a84e0a8db2fb0996c0be6be1f157d_1440w.jpg)

## 五、进阶选择：llama.cpp命令行部署（轻量高效，自定义性强）

如果你有一定的命令行基础，想追求更轻量的部署、更高的推理效率，或者想自定义模型参数，llama.cpp绝对是首选——一款轻量级的大模型推理框架，占用资源少，支持多平台，还能手动优化推理速度，适合进阶用户。  
重点说明：llama.cpp的核心优势是“轻量”，同样的硬件，用llama.cpp部署比其他工具更流畅，而且支持更多自定义参数，但需要用到命令行，稍微有点门槛，跟着步骤来也能轻松搞定。

### 具体部署步骤（以Windows系统为例，Mac/Linux类似）

**安装 [CUDA Toolkit](https://zhida.zhihu.com/search?content_id=271468771&content_type=Article&match_order=1&q=CUDA+Toolkit&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4MTI0MjksInEiOiJDVURBIFRvb2xraXQiLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNzE0Njg3NzEsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.szI7z3wgC2yFdaf1OWYK8GVigRsuDqiqdjThHpRtO1o&zhida_source=entity)**

1. 打开NVIDIA官方的下载链接，然后下载对应版本的CUDA：

[developer.nvidia.com/cu](https://link.zhihu.com/?target=https%3A//developer.nvidia.com/cuda-toolkit-archive)  
这里不知道自己显卡对应CUDA版本的，可以按下 `Win + R` 然后输入 `cmd` 打开命令行，输入 `nvidia-smi` 即可查看  
Driver Version：显示显卡驱动版本

CUDA Version：显示显卡支持的最高CUDA版本

![](https://pica.zhimg.com/v2-d2da114a9c3fceee77b9d22135ab88d0_1440w.jpg)

可以看到我的显卡支持的最高版本是13.2，所以我直接下载13.2以下的版本的即可，这里建议选择低一个版本，因为llama.cpp可能还没支持最新版。

![](https://pic3.zhimg.com/v2-692d582fa626b4d594333b9eac82184e_1440w.jpg)

选择相应的环境，然后点击下载即可

![](https://picx.zhimg.com/v2-d092d89172bea69f2b4cd36079a94ca3_1440w.jpg)

2\. 安装CUDA

双击下载的exe文件，许可协议，点击同意并继续

![](https://pic1.zhimg.com/v2-a8ee6c6362040a2e601d2885926b368e_1440w.jpg)

进入选项选择自定义。选择需要安装的组件，这里如果只是拿CUDA跑AI模型，不做CUDA开发，推荐最小化安装，如果你要写 CUDA 代码、做性能调优，保持默认全选即可，所有开发 / 调试 / 分析工具都会装上。

![](https://pic4.zhimg.com/v2-a804a12c964bd570f46f9475a29c6027_1440w.jpg)

选择安装位置，如果C盘至少有10GB空闲，建议默认即可，因为兼容性最好，绝大多数脚本、AI 框架（如 PyTorch、llama.cpp）会自动识别，减少后续环境配置的坑。并且系统环境变量会自动生成，不需要手动修改太多。如果按照在其他盘需要手动需要系统环境变量，并且安装路径不能包含中文。

![](https://pic1.zhimg.com/v2-607addd82c6939c6adacc9d586106366_1440w.jpg)

点击下一步，等待安装完成关闭即可

![](https://pic1.zhimg.com/v2-8ebe777225b3f979f1b07240fd2889b6_1440w.jpg)

3\. 验证CUDA是否安装成功

安装完成后重启Windows PowerShell,输入 `nvcc --version` 查看版本，出现版本信息即代表成功。

![](https://pic1.zhimg.com/v2-0cd5d4d7ab37d20e3801133308d826b6_1440w.jpg)

**下载llama.cpp  
**

1. 打开GitHub仓库（ [github.com/ggerganov/ll](https://link.zhihu.com/?target=https%3A//github.com/ggerganov/llama.cpp) ），点击“Release”
![](https://pic1.zhimg.com/v2-b4b6f37b3cd14794042172e11e5f6972_1440w.jpg)

然后根据自己的显卡和CUDA版本来选择

![](https://pic1.zhimg.com/v2-8a010c13f765f3407ae4343868baae38_1440w.jpg)

1. 配置环境：

Windows用户：双击解压文件夹，进去后右键点击在终端中打开

![](https://pica.zhimg.com/v2-e879d726a9bc1b547ca74675f0ef5cd4_1440w.jpg)

输入`.\llama-server.exe --list-devices` 查看显卡是否可用，输出显卡信息就说明OK。

![](https://pic2.zhimg.com/v2-46fd91ee0379bfefc06257027d13d83d_1440w.jpg)

然后输入

```bash
#-m参数为指定模型路径，后面跟模型路径即可
# -ngl 99是把负载加载到显存
.\llama-server.exe -m D:\info\model\Qwen3.5-9B-Q5_K_M.gguf -ngl 99
```

回车后等待加载一下，看到

` server is listening on http://127.0.0.1:8080`

就说明启动成功了，

![](https://pic2.zhimg.com/v2-e3e3a35c0b25c6fd90f46927b97c7f33_1440w.jpg)

然后我们按住Ctrl点击该链接，就可以打开UI界面了。

![](https://pic3.zhimg.com/v2-e6fdc26926360057d0119b605f701fa6_1440w.jpg)

如果需要关闭服务，关闭Windows PowerShell界面或者使用Ctrl C快捷键停止即可。  
最后附上一份核心基础启动参数列表

| 参数 | 说明 | 示例 |
| --- | --- | --- |
| \-m/--model | 指定模型文件路径（.gguf 格式，llama.cpp 主流格式） | \-m D:\\models\\qwen-7b-q4\_0.gguf |
| \-c/--ctx-size | 上下文窗口大小（决定模型能记住的对话长度，单位：tokens）最大模型回复的速度越慢 | \-c 4096（常用值：2048/4096/8192，需匹配模型支持的最大 ctx） |
| \-n/--n-predict | 单次生成的最大 tokens 数（回答的最大长度） | \-n 2048（设为 -1 则无限制，直到模型停止生成） |
| \-t/--threads | 启用的 CPU 线程数（建议设为 CPU 核心数的 70%-90%） | \-t 16（8 核 CPU 设 8，16 核设 12-16） |
| \-ngl/--n-gpu-layers | 卸载到 GPU 的层数（核心！利用显卡加速，值越大越省 CPU） | \-ngl 35（新手建议从 20/30 开始试，拉满设为 99） |
| \-b/--batch-size | 批处理大小（影响推理速度，建议设为 ctx-size 的 1/4~1/2） | \-b 1024（ctx=4096 时设 1024 较合适） |

## 六、常见问题FAQ（新手必看，解决90%的问题）

1. Q：加载模型时提示“显存不足”怎么办？ A：换更小参数量的模型（比如从13B换成7B），或选择更低量化版本（比如从Q5\_K\_M换成Q4\_K\_M），同时关闭其他占用显存的软件（比如游戏、视频剪辑软件）。
2. Q：CPU推理速度太慢，每秒只有1-2个token怎么办？ A：如果有GPU，开启硬件加速（LMStudio在设置中开启，llama.cpp添加“-ngl”参数）；Mac用户无需额外操作，Apple Silicon芯片会自动优化；纯CPU用户建议换7B Q2\_K量化版，速度会提升不少。
3. Q：从魔塔社区下载的模型，LMStudio加载不了怎么办？ A：检查模型格式是否为GGUF，不是的话重新下载；如果是GGUF格式，尝试重启LMStudio，或检查模型文件是否下载完整（中途中断会导致文件损坏）。
4. Q：部署完成后，断网能用吗？ A：可以！部署完成后，所有模型文件都在本地，完全不依赖网络，断网后正常对话、生成内容都没问题。
5. Q：本地部署的大模型，效果和云端GPT-4差距大吗？ A：7B量化版适合日常使用，复杂推理、深度问答不如GPT-4；但13B及以上版本，配合高质量模型（比如Llama3.1-8B、Qwen2.5-13B），效果接近云端中端模型，足够满足大多数人的需求。

编辑于 2026-03-14 17:37・湖南[本地部署大模型](https://www.zhihu.com/topic/29897692)[有了豆包学习搭子，作文、翻译、讲解，学习轻松无压力](http://www.doubao.com/download/desktop?ug_apk_token=LQqwd&ad_platform_id=zhihu_feed_lead&ug_callback_url=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D9890daea-21f8-4dfe-89f6-ae2d819c23d2%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&cb=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D9890daea-21f8-4dfe-89f6-ae2d819c23d2%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&ug_semver=v1.0.0&spu=biz%3D0%26ci%3D3751285%26si%3D5b9d7f06-c378-4e02-b1d1-5b57548d6fa1%26ts%3D1782639631%26zid%3D1629)

[

学生党学习搭子-豆包AI！不仅可以输出中英文作文、英语翻译、作文修改润色，还能有海量题目讲解

](http://www.doubao.com/download/desktop?ug_apk_token=LQqwd&ad_platform_id=zhihu_feed_lead&ug_callback_url=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D9890daea-21f8-4dfe-89f6-ae2d819c23d2%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&cb=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D9890daea-21f8-4dfe-89f6-ae2d819c23d2%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&ug_semver=v1.0.0&spu=biz%3D0%26ci%3D3751285%26si%3D5b9d7f06-c378-4e02-b1d1-5b57548d6fa1%26ts%3D1782639631%26zid%3D1629)

赞同 24