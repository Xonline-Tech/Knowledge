category:: Notes
tags:: Alpine

-
- ### [[清华大学开源软件镜像站]]
	- > [帮助文档](https://mirrors.tuna.tsinghua.edu.cn/help/alpine/)
	- 在终端输入以下命令以替换镜像源：
		- ```
		  sed -i 's#https\?://dl-cdn.alpinelinux.org/alpine#https://mirrors.tuna.tsinghua.edu.cn/alpine#g' /etc/apk/repositories
		  ```
	- 也可以直接编辑 `/etc/apk/repositories` 文件。以下是 v3.5 版本的参考配置：
		- ```
		  https://mirrors.tuna.tsinghua.edu.cn/alpine/v3.5/main
		  https://mirrors.tuna.tsinghua.edu.cn/alpine/v3.5/community
		  ```
	- > 也可以使用 `latest-stable` 指向最新的稳定版本：
	  ```
	  https://mirrors.tuna.tsinghua.edu.cn/alpine/latest-stable/main
	  https://mirrors.tuna.tsinghua.edu.cn/alpine/latest-stable/community
	  ```
	- 更改完 `/etc/apk/repositories` 文件后请更新索引以使更改生效：
		- ```
		  apk update
		  ```
- # 接下来
	- [[在Alpine中安装Docker与Compose]]