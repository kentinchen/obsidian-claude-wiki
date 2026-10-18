npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code --allow-scripts=@anthropic-ai/claude-code
claude --version

npm install -g @openai/codex --registry=https://registry.npmmirror.com
npm install -g @openai/codex  --allow-scripts=@openai/codex
codex --help 
codex --version

zhishile/codex-auth-helper: Codex登陆助手
mv ~/Downloads/auth.json ~/.codex/auth.json
chmod 600 ~/.codex/auth.json

npm install -g opencode-ai --allow-scripts=opencode-ai
opencode --help

irm https://trae.cn/trae-cli/install_v2.ps1 | iex

安装orca
npx skills add https://github.com/stablyai/orca --skill orca-cli --skill orchestration --global
npx skills add https://github.com/stablyai/orca --skill computer-use --global

https://openrouter.ai
https://openrouter.ai/api/v1
openrouter/free
https://integrate.api.nvidia.com/v1

cpolar-tunnel创建动态端口转发，参数为 33895:172.63.132.33:3389 38080:172.62.130.33:8080
Base URL: http://localhost:38080/v1
上游协议：Chat Completions


curl -fsSL "https://github.com/Alishahryar1/free-claude-code/blob/main/scripts/install.sh?raw=1" | sh
irm "https://github.com/Alishahryar1/free-claude-code/blob/main/scripts/install.ps1?raw=1" | iex
fcc-server
fcc-claude
http://127.0.0.1:8082/admin


npm install -g teamai-cli
teamai init https://github.com/yourorg/yourrepo                         #项目级
teamai init https://github.com/yourorg/yourrepo --scope user    #用户级
teamai push
teamai pull

teamai hooks list      # 查看生效的 hooks
teamai hooks inject    # 重新注入到每个已安装的工具
teamai hooks remove
teamai mcp list | inject | remove
teamai source list
teamai source browse other-team    # 浏览可用 skills
teamai source remove other-team

rtk init -g --codex

hf download hf://lmstudio-community/Bonsai-27B-GGUF/Bonsai-27B-Q1_0.gguf
OpenAI Chat Completions 格式
http://127.0.0.1:1234/v1
bonsai-27b

npx skills add tt-a1i/archify -g
npx -y skills add tt-a1i/archify --skill archify --agent codex --global --copy --yes
npx -y skills add tt-a1i/archify --skill archify --agent codex --copy --yes


npm install -g cc-connect
cc-connect --version
cc-connect weixin setup --project home-claude
cc-connect feishu setup  --project home-claude  --app cli_xxx:sec_xxx
- `home-claude` 是项目名称；
- `cli_xxx` 替换为飞书 App ID；
- `sec_xxx` 替换为飞书 App Secret
cc-connect daemon restart
cc-connect web
cc-connect daemon install --config ~/.cc-connect/config.toml 
cc-connect daemon start
查看服务状态 
cc-connect daemon status 
实时查看日志 
cc-connect daemon logs -f 
重启服务 
cc-connect daemon restart 
停止服务 
cc-connect daemon stop


~/.cc-connect/config.toml
为不同项目创建独立配置
[[projects]] 
name = "main-project"
[projects.agent] 
type = "claudecode"
[projects.agent.options] 
work_dir = "/Users/you/Workspace/main-project" 
mode = "default"

[[projects]] 
name = "blog" 
[projects.agent] 
type = "claudecode"
[projects.agent.options] 
work_dir = "/Users/you/Workspace/blog" 
mode = "default"

  