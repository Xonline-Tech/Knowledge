category:: Software
type:: 开发🔨

- # 安装&初始化
	- ## 安装
		- ### 在 [[Windows]] 中安装
			- #### 方法一、通过 [[WSL]] 使用 OpenCode (推荐)
				- > **先决条件：**完成 [[WSL]] 系统安装并初始
				- 在WSL系统中安装
					- ```shell
					  curl -fsSL https://opencode.ai/install | bash
					  ```
			-
	- ## 初始化配置
		-
- ## [安装](https://opencode.ai/docs/zh-cn/#安装)
	- 安装 OpenCode 最简单的方法是通过安装脚本。
	- ```
	  curl -fsSL https://opencode.ai/install | bash
	  ```
	- 你也可以使用以下方式安装：
		- **使用 Node.js**
			- npm
			- ```
			  npm install -g opencode-ai
			  ```
		- **在 macOS 和 Linux 上使用 [[Homebrew]]**
			- ```
			  brew install anomalyco/tap/opencode
			  ```
			- > 我们推荐使用 OpenCode tap 以获取最新版本。官方的 `brew install opencode` formula 由 Homebrew 团队维护，更新频率较低。
		- **在 Arch Linux 上安装**
			- ```
			  sudo pacman -S opencode           # Arch Linux (Stable)
			  paru -S opencode-bin              # Arch Linux (Latest from AUR)
			  ```
	- #### [Windows](https://opencode.ai/docs/zh-cn/#windows)
		- 推荐：使用 WSL
		- 为了在 Windows 上获得最佳体验，我们推荐使用 [Windows Subsystem for Linux (WSL)](https://opencode.ai/docs/windows-wsl)。它提供更好的性能，并完全兼容 OpenCode 的所有功能。
			- **使用 Chocolatey**
				- ```
				      choco install opencode
				    ```
			- **使用 Scoop**
				- ```
				      scoop install opencode
				    ```
			- **使用 NPM**
				- ```
				      npm install -g opencode-ai
				    ```
			- **使用 Mise**
				- ```
				      mise use -g github:anomalyco/opencode
				    ```
			- **使用 Docker**
				- ```
				      docker run -it --rm ghcr.io/anomalyco/opencode
				    ```
		- 在 Windows 上通过 Bun 安装 OpenCode 的支持目前正在开发中。
		- 你也可以从 [Releases](https://github.com/anomalyco/opencode/releases) 页面直接下载二进制文件。