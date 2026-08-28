# 使用
	- ## 重建仓库缓存
		- ```shell
		  sudo dnf clean all
		  sudo dnf makecache
		  ```
	- ## 检查软件更新
		- ```shell
		  # 检查全部软件更新
		  dnf check-upgrade
		  
		  # 检查单个软件是否有更新
		  dnf check-upgrade xxx
		  # 检查单个软件更新的更详细的信息
		  dnf info --upgrades xxx
		  
		  # 更新单个或多个软件
		  sudo dnf upgrade
		  sudo dnf upgrade xxx
		  ```
	-