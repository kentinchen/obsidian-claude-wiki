powershell -c "irm bun.sh/install.ps1|iex"

git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup

npm install -g @fission-ai/openspec --allow-scripts=@fission-ai/openspec
openspec init
openspec update

/opsx-propose "创建一个后台管理程序，主要功能是定时采集数据，然后保存到数据库中，web界面上确认数据无误之后，点击发送或自动定时发送到云管服务器"
/opsx:apply
/opsx:sync 
/opsx:archive

openspec list
openspec view


npm install -g @studyzy/openspec-cn
npm install -g @fission-ai/openspec@latest
npm install -g @openai/codex@0.116.0
openspec init --tools codex
openspec-cn init --tools codex

https://github.com/obra/superpowers
https://openspec.dev/
第一步，写清项目上下文。
至少准备好 README 和 AGENTS.md。告诉 Codex 项目是什么、技术栈是什么、目录怎么分工、常用命令是什么、哪些边界不能碰。
第二步，用 Superpowers 的 brainstorming 先讨论需求。
不要一句话直接开写。让 Codex 先问你问题，把用户、场景、边界、第一版范围和验收标准问清楚。
第三步，用 OpenSpec / SDD 写规格和任务。
让它先列出这次改什么、不改什么、怎么拆任务、怎么验证。规格确认后再实现。
第四步，小步实现。
每次只推进一件事。尽量控制文件范围，避免一次性改后端、前端、移动端、测试和文档。
第五步，用 Superpowers 的 TDD 和 verification 收尾。
让 Codex 跑相关命令，说明验证结果。你自己也要读 diff、看页面、跑关键流程。最后确认的不只是代码，而是业务结果。

创建变更	$openspec-propose	        生成 proposal.md、design.md、tasks.md 等
实施变更	$openspec-apply-change	    按规范文档生成代码
验证实现	$openspec-verify-change	    校验代码是否与规范对齐
归档变更	$openspec-archive-change	完成后归档，更新主文档
探索调研	$openspec-explore	        探索和调研需求想法