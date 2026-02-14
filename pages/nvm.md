category:: Software
description:: nvm 是一个用于管理 Node.js 版本的命令行工具，可以在同一台机器上安装和切换多个版本的 Node.js。

- # 安装&初始化
	- ## 安装
		- > 需要提前安装 [[curl]]
		- ```shell
		  # 执行脚本
		  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
		  
		  # 编辑配置文件 根据自己使用的shell选择配置文件
		  vi ~/.bash_profile
		  # 在结尾添加
		  export NVM_DIR="$HOME/.nvm"
		  [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
		  [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
		  
		  
		  ```