category:: Notes
tags:: Debian

- ### [[清华大学开源软件镜像站]]
	- > [帮助文档](https://mirrors.tuna.tsinghua.edu.cn/help/debian/)
	- 大部分 Debian 的软件源配置文件使用传统的 One-Line-Style，路径为 `/etc/apt/sources.list`；但是对于容器镜像，从 Debian 12 开始，其软件源配置文件变更为 DEB822 格式，路径为 `/etc/apt/sources.list.d/debian.sources`。一般情况下，将对应文件中 Debian 默认的源地址 `http://deb.debian.org/` 替换为镜像地址即可。
		- > Debian Buster 以上版本默认支持 HTTPS 源。如果遇到无法拉取 HTTPS 源的情况，请先使用 HTTP 源并安装：
		  ```shell
		  sudo apt install apt-transport-https ca-certificates
		  ```
	- 修改文件`/etc/apt/sources.list`
	- ```bash
	      sed -e 's|^metalink=|#metalink=|g' \
	      	      -e 's|^#baseurl=http://download.example/pub/fedora/linux|baseurl=https://mirrors.tuna.tsinghua.edu.cn/fedora|g' \
	      	      -i.bak \
	      	      /etc/yum.repos.d/fedora.repo \
	      	      /etc/yum.repos.d/fedora-updates.repo
	    ```