category:: Notes
tags:: RPMFusion

- ### [[清华大学开源软件镜像站]]
	- > [帮助文档](https://mirrors.tuna.tsinghua.edu.cn/help/rpmfusion/)
	- 安装成功后，使用以下命令修改 `/etc/yum.repos.d/` 目录下以 `rpmfusion` 开头，以 `.repo` 结尾的文件：
	- ```shell
	  sed -e 's!^metalink=!#metalink=!g' \
	           -e 's!^mirrorlist=!#mirrorlist=!g' \
	           -e 's!^#baseurl=!baseurl=!g' \
	           -e 's!https\?://download1\.rpmfusion\.org/!https://mirrors.tuna.tsinghua.edu.cn/rpmfusion/!g' \
	           -i.bak /etc/yum.repos.d/rpmfusion*.repo
	  ```