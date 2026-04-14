category:: Notes
tags:: Debian

- ### [[清华大学开源软件镜像站]]
	- > [帮助文档](https://mirrors.tuna.tsinghua.edu.cn/help/debian/)
	- 大部分 Debian 的软件源配置文件使用传统的 One-Line-Style，路径为 `/etc/apt/sources.list`；但是对于容器镜像，从 Debian 12 开始，其软件源配置文件变更为 DEB822 格式，路径为 `/etc/apt/sources.list.d/debian.sources`。一般情况下，将对应文件中 Debian 默认的源地址 `http://deb.debian.org/` 替换为镜像地址即可。
		- > Debian Buster 以上版本默认支持 HTTPS 源。如果遇到无法拉取 HTTPS 源的情况，请先使用 HTTP 源并安装：
		  ```shell
		  sudo apt install apt-transport-https ca-certificates
		  ```
	- 参照示例修改文件 `/etc/apt/sources.list`
		- ```shell
		  # 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
		  deb https://mirrors.tuna.tsinghua.edu.cn/debian/ trixie main contrib non-free non-free-firmware
		  # deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ trixie main contrib non-free non-free-firmware
		  
		  deb https://mirrors.tuna.tsinghua.edu.cn/debian/ trixie-updates main contrib non-free non-free-firmware
		  # deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ trixie-updates main contrib non-free non-free-firmware
		  
		  deb https://mirrors.tuna.tsinghua.edu.cn/debian/ trixie-backports main contrib non-free non-free-firmware
		  # deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ trixie-backports main contrib non-free non-free-firmware
		  
		  # 以下安全更新软件源包含了官方源与镜像站配置，如有需要可自行修改注释切换。
		  # 为了保证安全更新的时效性，Debian 不推荐用户使用安全更新镜像，如确需使用请选择同步频次较高的镜像站。
		  # deb https://security.debian.org/debian-security trixie-security main contrib non-free non-free-firmware
		  # deb-src https://security.debian.org/debian-security trixie-security main contrib non-free non-free-firmware
		  deb https://mirrors.tuna.tsinghua.edu.cn/debian-security trixie-security main contrib non-free non-free-firmware
		  # deb-src https://mirrors.tuna.tsinghua.edu.cn/debian-security trixie-security main contrib non-free non-free-firmware
		  ```
-