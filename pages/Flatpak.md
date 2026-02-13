category:: Software
type:: Package-Manage

- # 安装&初始化
	- ## 安装
		- [[Debian]] / [[Ubuntu]] - [[apt]]
			- ```
			  sudo apt install flatpak
			  ```
		- [[RHEL]]系列 - [[yum]] / [[dnf]]
			- ```
			  sudo dnf install flatpak
			  ```
		- [[ArchLinux]] / [[Manjaro]] - [[pacman]]
			- ```
			  sudo pacman -S flatpak
			  ```
	- ## 初始化配置
		- 添加 Flathub 官方仓库
			- ```
			  flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
			  ```
- # 接下来
	- [[Flatpak切换国内镜像源]]
	- 使用 [[FlatSeal]]管理与配置Flatpak安装的软件