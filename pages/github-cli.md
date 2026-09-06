alias:: gh
website:: [官网](https://cli.github.com/)
description:: `gh`是命令行中的GitHub。它会把拉取请求、问题和其他GitHub概念带到你正在处理`git`的终端和代码旁边。

- # 安装
	- ### [[Fedora]] / [[RHEL]] - [[dnf5]]
		- ```shell
		  sudo dnf install dnf5-plugins
		  sudo dnf config-manager addrepo --from-repofile=https://cli.github.com/packages/rpm/gh-cli.repo
		  sudo dnf install gh
		  ```
	- ### [[Fedora]] / [[RHEL]] - [[dnf4]]
		- ```shell
		  sudo dnf install 'dnf-command(config-manager)'
		  sudo dnf config-manager --add-repo https://cli.github.com/packages/rpm/gh-cli.repo
		  sudo dnf install gh
		  ```