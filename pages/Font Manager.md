alias:: font-manager
category:: Software
type:: 系统⚙️
website:: [官网](https://fontmanager.github.io/) [Github](https://github.com/FontManager/font-manager)
description:: 适用于GTK桌面环境的简单字体管理应用程序
os:: Linux

- 字体管理器旨在为普通用户提供一种轻松管理桌面字体的方法,而无需使用命令行工具或手动编辑配置文件。虽然主要以Gnome桌面环境为设计,但应与其他GTK桌面环境配合良好。
- > 字体管理器不是专业级的字体管理解决方案。
- ## 特点
	- 预览和比较字体文件
	- 激活或停用已安装的字体系列
	- 基于字体属性的自动分类
	- 谷歌字体目录集成
	- 集成字符映射
	- 用户字体集合
	- 用户字体安装与删除
	- 用户字体目录设置
	- 用户字体替换设置
	- 桌面字体设置(GNOME 桌面或兼容环境)
- # 安装&初始化
	- ## 安装
		- ### [[Fedora]] / [[RHEL]] - [[yum]] / [[dnf]]
			- ```shell
			  # 使用 dnf 安装
			  sudo dnf copr enable jerrycasiano/FontManager
			  sudo dnf install font-manager
			  ```
		- ### [[Debian]] / [[Ubuntu]] - [[apt]]
			- ```shell
			  sudo add-apt-repository ppa:font-manager/staging
			  sudo apt-get update
			  sudo apt-get install font-manager
			  ```
		- ### [[ArchLinux]] / [[Manjaro]] - [[pacman]] / [[yay]]
			- ```
			  pacman -S font-manager
			  ```
			-