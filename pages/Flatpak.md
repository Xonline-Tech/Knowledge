category:: Software
type:: Package-Manage

- # 首次安装与使用
	- ## 安装
		- [[Debian]] / [[Ubuntu]] - [[apt]]
			- ```
			  sudo apt install flatpak
			  ```
		- [[RHEL]]系列 - [[yum]] / [[dnf]]
			- ```
			  sudo dnf install flatpak
			  ```
		- [[ArchLinux]]系列 - [[pacman]]
			- ```
			  sudo pacman -S flatpak
			  ```
	- ## 初始化配置
		- 添加 Flathub 官方仓库
			- ```
			  flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
			  ```