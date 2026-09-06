alias:: codex,codex-cli
category:: Software
vendors:: [[OpenAI]]
website:: [官网](https://chatgpt.com/zh-Hans-CN/codex/)

-
- # 安装
	-
- # 配置
	- ## 为Codex客户端与[[codex-cli]]配置代理服务
	  id:: 6a9c2c86-1169-4dff-b1d7-2602788d00ad
		- 给 Codex 自身单独配置代理
		  logseq.order-list-type:: number
			- ```shell
			  mkdir -p ~/.codex
			  
			  cat > ~/.codex/.env <<'EOF'
			  HTTP_PROXY=http://127.0.0.1:7890
			  HTTPS_PROXY=http://127.0.0.1:7890
			  
			  http_proxy=http://127.0.0.1:7890
			  https_proxy=http://127.0.0.1:7890
			  
			  NO_PROXY=localhost,127.0.0.1,::1
			  no_proxy=localhost,127.0.0.1,::1
			  EOF
			  
			  chmod 600 ~/.codex/.env
			  ```
		- 给 Codex 执行的 `git/curl/npm/pip` 等命令注入代理
		  logseq.order-list-type:: number
			- > [参考文档：https://learn.chatgpt.com/docs/config-file/config-reference](https://learn.chatgpt.com/docs/config-file/config-reference)
			- 编辑 `nano ~/.codex/config.toml` ，在你现有配置里加入：
			- ```
			  [shell_environment_policy]
			  inherit = "all"
			  - [shell_environment_policy.set]
			  HTTP_PROXY = "http://127.0.0.1:7890"
			  HTTPS_PROXY = "http://127.0.0.1:7890"
			  http_proxy = "http://127.0.0.1:7890"
			  https_proxy = "http://127.0.0.1:7890"
			  NO_PROXY = "localhost,127.0.0.1,::1"
			  no_proxy = "localhost,127.0.0.1,::1"
			  ```