category:: Software
type:: 互联网🌎
website:: [官网](https://www.microsoft.com/zh-cn/edge)

- # 安装&初始化
	- ## 安装
		- ### [[Fedora]] / [[RHEL]] - [[dnf]]
			- 添加密钥与源
				- ```shell
				  sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
				  
				  # for dnf4(fedora40-)
				  sudo dnf config-manager --add-repo https://packages.microsoft.com/yumrepos/edge/config.repo
				  
				  # for dnf5(fedora41+)
				  sudo dnf config-manager addrepo --from-repofile=https://packages.microsoft.com/yumrepos/edge/config.repo
				  ```
			- 安装
				- ```shell
				  sudo dnf install microsoft-edge-stable
				  ```