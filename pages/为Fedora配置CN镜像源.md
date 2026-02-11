category:: Notes
tags:: Fedora

-
- ### [[清华大学开源软件镜像站]]
	- > [帮助文档](https://mirrors.tuna.tsinghua.edu.cn/help/fedora/)
	- 用以下命令替换 `/etc/yum.repos.d` 下的文件
	- ```shell
	  sed -e 's|^metalink=|#metalink=|g' \
	      -e 's|^#baseurl=http://download.example/pub/fedora/linux|baseurl=https://mirrors.tuna.tsinghua.edu.cn/fedora|g' \
	      -i.bak \
	      /etc/yum.repos.d/fedora.repo \
	      /etc/yum.repos.d/fedora-updates.repo
	  ```
- # 接下来
	- 添加[[RPMFusion]]软件源或[[为RPMFusion配置CN镜像源]]
-