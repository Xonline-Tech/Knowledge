alias:: oh-my-opencode,oh-my-openagent
category:: plugins
upstream:: [[OpenCode]]

- # 安装
	- 默认安装
		- ```shell
		  bunx oh-my-openagent install --platform=opencode
		  ```
	- 指定环境安装
		- ```shell
		  OPENCODE_CONFIG_DIR="$HOME/.config/opencode-omo" \
		  bunx oh-my-openagent install --platform=opencode
		  ```