category:: Software
type:: 开发🔨
website:: [官网](https://opencode.ai/) [文档](https://opencode.ai/docs/zh-cn) [Github](https://github.com/anomalyco/opencode)

- # 安装&初始化
	- ## 安装
		- ### 在 [[Windows]] 中安装
			- #### 方法一、通过 [[WSL]] 使用 OpenCode (推荐)
				- > **先决条件：**完成 **WSL** 的 ((fee56816-f3e2-49d8-bf50-7bdf7732198b))
				- 进入WSL系统中并运行命令安装Opencode
					- ```shell
					  curl -fsSL https://opencode.ai/install | bash
					  ```
			- #### 方法二、通过 [[NPM]] 运行 OpenCode
				- ```shell
				  npm install -g opencode-ai
				  ```
			- #### 方法三、通过 [[scoop]] 运行 OpenCode
				- ```shell
				  scoop install opencode
				  ```
			- #### 方法四、通过 [[Chocolatey]] 运行 OpenCode
				- ```shell
				  choco install opencode
				  ```
		- ### 在 [[MacOS]] 与 [[Linux]] 中安装
			- #### 使用 [[Homebrew]] 安装
				- ```shell
				  brew install anomalyco/tap/opencode
				  ```
				- > 我们推荐使用 OpenCode tap 以获取最新版本。官方的 `brew install opencode` formula 由 Homebrew 团队维护，更新频率较低。
			- ### [[ArchLinux]] / [[Manjaro]] - [[pacman]] / [[yay]]
				- ```shell
				  sudo pacman -S opencode           # Arch Linux (Stable)
				  paru -S opencode-bin              # Arch Linux (Latest from AUR)
				  ```
	- ## 初始化配置
		- > **在 WSL 中启动服务器**，添加 `--hostname 0.0.0.0` 以允许外部连接**
		  警告:使用 `--hostname 0.0.0.0` 时，请设置 `OPENCODE_SERVER_PASSWORD` 以保护服务器安全。**
		  ```shell
		  OPENCODE_SERVER_PASSWORD=your-password opencode serve --hostname 0.0.0.0
		  ```
		- ### TUI直接使用
			- 进入项目源码路径，直接输入 `opencode`
		- ### 作为服务端使用（桌面应用 + WSL 服务器）
			- ```shell
			  opencode serve --port 4096
			  ```
			- 在桌面应用中连接到 `http://localhost:4096`
		- ### 在Web客户端使用
			- ```shell
			  opencode web
			  ```