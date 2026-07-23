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

dingw3ri52mgr9e8grv3
PV20HCTMoL5Kelx-N4YSU9ypK3VGmVNMRq3W1wdpgUzkKZ94EL-Jz1MzCG8l4jKg

hermes gateway restart
hermes gateway status
Get-Content "$env:LOCALAPPDATA\hermes\logs\gateway.log" -Wait -Tail 5