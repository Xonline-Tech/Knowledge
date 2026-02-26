# 开发环境部署
	- ## 基础环境准备
		- ### Linux基础软件包
			- [[RHEL]]系列 - [[yum]] / [[dnf]]
				- ```shell
				  sudo dnf install curl git wget unzip xz zip mesa-libGLU clang cmake ninja-build pkg-config gtk3-devel
				  ```
	- ## 安装Android Studio
		- 安装 [[Android Studio]]并根据文档安装相关工具包
	- ## 安装FlutterSDK
		- ### 下载
			- ```shell
			  mkdir -pv ~/.sdk
			  cd ~/.sdk
			  git clone https://github.com/flutter/flutter.git -b stable
			  ```
		- ### 配置环境变量
			- ```shell
			  vi ~/.bashrc
			  
			  ## 在下方追加配置
			  export PATH="$PATH:$HOME/.sdk/flutter/bin"
			  ```
		- ### 接受AndroidSDK证书
			- ```shell
			  flutter doctor --android-licenses
			  ```
	- ## 配置国内镜像源（可选）
		- ```shell
		  vi ~/.bashrc
		  
		  ## 在下方追加配置
		  export PUB_HOSTED_URL=https://mirrors.tuna.tsinghua.edu.cn/dart-pub
		  export FLUTTER_STORAGE_BASE_URL=https://mirrors.tuna.tsinghua.edu.cn/flutter
		  ```
	- ## Chrome浏览器配置
		- ```shell
		  which chromium-browser
		  # 临时测试
		  export CHROME_EXECUTABLE=/usr/bin/chromium-browser
		  
		  # 再次测试
		  flutter doctor
		  
		  # 永久配置
		  vi ~/.bashrc
		  
		  ## 在下方追加配置
		  export CHROME_EXECUTABLE=/usr/bin/chromium-browser
		  ```