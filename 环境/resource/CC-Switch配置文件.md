
hermes配置文件
{
  "name": "openrouter",
  "base_url": "https://openrouter.ai/api/v1",
  "api_key": "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",
  "api_mode": "chat_completions",
  "models": [
    {
      "id": "nvidia/nemotron-3-super-120b-a12b:free",
      "name": "nvidia/nemotron-3-super-120b-a12b:free",
      "context_length": 1000000
    }
  ]
}

{
  "name": "omniroute",
  "base_url": "http://localhost:20128/v1",
  "api_key": "local",
  "models": [
    {
      "id": "free",
      "name": "free"
    }
  ]
}

{
  "name": "",
  "base_url": "http://172.62.130.33:8080/v1",
  "api_key": "sk-3eda773f71924d64b8fb9eb772d4ed07",
  "models": [
    {
      "id": "Qwen3.6-27B",
      "name": "Qwen3.6-27B"
    }
  ]
}

claude code配置文件
{
  "enabledPlugins": {
    "claude-mem@thedotmack": true
  },
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "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",
    "ANTHROPIC_BASE_URL": "https://openrouter.ai/api",
    "ANTHROPIC_DEFAULT_FABLE_MODEL": "qwen/qwen2.5-coder-14b",
    "ANTHROPIC_DEFAULT_FABLE_MODEL_NAME": "qwen/qwen2.5-coder-14b",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "nvidia/nemotron-3-super-120b-a12b:free",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "nvidia/nemotron-3-super-120b-a12b:free",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "nvidia/nemotron-3-super-120b-a12b:free",
    "ANTHROPIC_MODEL": "nvidia/nemotron-3-super-120b-a12b:free",
    "ANTHROPIC_REASONING_MODEL": "nvidia/nemotron-3-super-120b-a12b:free"
  },
  "extraKnownMarketplaces": {
    "obsidian-skills": {
      "source": {
        "repo": "kepano/obsidian-skills",
        "source": "github"
      }
    },
    "thedotmack": {
      "source": {
        "repo": "thedotmack/claude-mem",
        "source": "github"
      }
    }
  },
  "includeCoAuthoredBy": false,
  "skipWebFetchPreflight": true
}