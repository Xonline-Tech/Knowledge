category:: Notes
tags:: dnf,config-manager,fedora

- ## 关于Fedora 40或更早（[[DNF 4]]）
	- 要添加一个新的仓库，作为**root** ，请使用以下方法之一。
	- 通过在临时位置（如目录`/tmp`）创建带有`.repo`后缀的新文件来定义一个新的仓库。
	- 将存储库添加为 `--add-repo` ，其中 ***repository*** 是文件路径：
		- ```
		  dnf config-manager --add-repo ***repository***
		  ```
		  例如：
		  ```
		  dnf config-manager --add-repo /tmp/fedora_extras.repo
		  ```
- ## 关于Fedora 41及以后版本（[[DNF 5]]）
	- 要添加一个新的仓库，作为 **root**，请使用以下方法之一。
	- 通过在临时位置（如目录`/tmp`）创建带有后缀`.repo`的新文件来定义一个新的仓库。
	- 将存储库添加为 `addrepo`，其中 ***repository*** 是文件路径：
		- ```
		  dnf config-manager addrepo --from-repofile=***repository***
		  ```
		  例如：
		  ```
		  dnf config-manager addrepo --from-repofile=/tmp/fedora_extras.repo
		  ```