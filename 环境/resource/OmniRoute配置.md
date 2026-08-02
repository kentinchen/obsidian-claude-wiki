omniroute                                     # 启动网关
http://localhost:20128 
http://127.0.0.1:20128/v1/models
omniroute setup-claude               # 一键配置 Claude Code 走 OmniRoute

1、配置注册密钥      http://localhost:20128/dashboard/api-manager
2、配置模型提供商   http://localhost:20128/dashboard/providers
	url:  http://172.62.68.240:8080/v1
	vpc: http://172.62.130.33:8080/v1
	sk-3eda773f71924d64b8fb9eb772d4ed07
	Qwen3.6-27B
	curl http://172.62.130.33:8080/v1/models -H "Authorization: Bearer sk-3eda773f71924d64b8fb9eb772d4ed07"
	
	https://openrouter.ai
	https://openrouter.ai/api
	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
	nvidia/nemotron-3-super-120b-a12b:free

3、创建组合             http://localhost:20128/dashboard/combos
4、在cc switch中使用组合名字作为Agent的模型


NODE_OPTIONS=--max-old-space-size=4096
[DB] Could not probe existing DB: out of memory
omniroute stop
omniroute repair
omniroute runtime repair