C:\Users\Administrator\AppData\Local\hermes\config.yaml
%LOCALAPPDATA%\hermes\config.yaml
%LOCALAPPDATA%\hermes\profiles\<profile-name>\config.yaml

custom_providers:
  - name: openroute
    base_url: https://openrouter.ai/api/v1
    api_key: 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
    api_mode: chat_completions
    models:
      nvidia/nemotron-3-super-120b-a12b:free:
        context_length: 1000000
        name: nvidia/nemotron-3-super-120b-a12b:free
    model: nvidia/nemotron-3-super-120b-a12b:free
  - name: omniroute
    base_url: http://localhost:20128/v1
    api_key: local
    models:
      auto/best-coding:
        name: auto/best-coding
      auto/chat:
        name: auto/chat
    model: auto/best-coding

hermes dashboard
http://localhost:9119/sessions

hermes config get dingtalk
hermes gateway setup
hermes gateway restart
hermes gateway status
Get-Content "$env:LOCALAPPDATA\hermes\logs\gateway.log" -Wait -Tail 5

C:\Users\Administrator\AppData\Local\hermes\.env
FEISHU_APP_ID=cli_aadd2183ce38dcc8
FEISHU_APP_SECRET=Yt1Rs0XswcvwjjFbCiFpTcbufMoFJieE
FEISHU_ALLOW_ALL_USERS=true
FEISHU_DOMAIN=feishu
FEISHU_HOME_CHANNEL_NAME=hermes

DINGTALK_CLIENT_ID=dingmdyg7qt5se5y5cbc
DINGTALK_CLIENT_SECRET=J8e2GSS-9PJxeEvXf9fctx6f5ErtIxt1p3_CmMgZ_H8VAox-9KOKz0Rg-77tjqkU
DINGTALK_HOME_CHANNEL_NAME=default
DINGTALK_ALLOWED_USERS=*
DINGTALK_ALLOW_ALL_USERS=true

运行 `hermes gateway setup` → 在平台列表选 Weixin → 用微信手机端扫终端二维码 → 在手机上确认登录 → Hermes 自动保存 `account_id` / `token` / `base_url` → 配好 `WEIXIN_ACCOUNT_ID` → 运行 `hermes gateway`。走的是 iLink Bot API + HTTP 长轮询，不需要公网回调。

	hermes config                 View configuration
    hermes config edit            Edit config in $EDITOR
    hermes config set model gpt-4 Set a config value
    hermes logout                 Clear stored authentication
    hermes auth add <provider>    Add a pooled credential
    hermes auth list              List pooled credentials
    hermes auth remove <p> <t>    Remove pooled credential by index, id, or label
    hermes auth reset <provider>  Clear exhaustion status for a provider
    hermes logs                   View agent.log (last 50 lines)
    hermes logs -f                Follow agent.log in real time
    hermes logs errors            View errors.log
    hermes logs --since 1h        Lines from the last hour
    hermes update                 Update to latest version
    hermes dashboard              Start web UI dashboard (port 9119)