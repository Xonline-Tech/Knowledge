website:: https://rpmfusion.org/

- # 安装&初始化
	- 首先安装提供基础配置文件和 GPG 密钥的 `rpmfusion-*.rpm`。
	- ### [[Fedora]] 用户
		- ```
		  yum install --nogpgcheck http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
		  ```
		- 或者如下直接用镜像中的 rpm 包：
		- ```
		  yum install --nogpgcheck https://mirrors.tuna.tsinghua.edu.cn/rpmfusion/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.tuna.tsinghua.edu.cn/rpmfusion/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
		  ```
	- ### [[CentOS]]/[[RHEL]] 用户
		- ```shell
		  yum localinstall --nogpgcheck https://mirrors.tuna.tsinghua.edu.cn/rpmfusion/free/el/rpmfusion-free-release-8.noarch.rpm https://mirrors.tuna.tsinghua.edu.cn/rpmfusion/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm
		  ```