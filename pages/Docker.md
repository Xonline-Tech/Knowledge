alias:: docker
category:: Software

- # 安装&初始化
	- ## 安装
		- ### [[Debian]] / [[Ubuntu]] - [[apt]]
			- 更新系统并安装依赖
			  logseq.order-list-type:: number
				- ```
				  sudo apt update
				  sudo apt install -y ca-certificates curl
				  ```
			- 添加 Docker 官方 GPG 密钥
			  logseq.order-list-type:: number
				- ```shell
				  sudo install -m 0755 -d /etc/apt/keyrings
				  sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
				  sudo chmod a+r /etc/apt/keyrings/docker.asc
				  ```
			- 将 Docker 源添加到 APT 源列表
			  logseq.order-list-type:: number
				- > 下方源选一个
				- **Docker源-官方**
					- ```shell
					  sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
					  Types: deb
					  URIs: https://download.docker.com/linux/debian
					  Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
					  Components: stable
					  Signed-By: /etc/apt/keyrings/docker.asc
					  EOF
					  ```
				- **Docker源-[[清华大学开源软件镜像站]] [帮助](https://mirrors.tuna.tsinghua.edu.cn/help/docker-ce/)**
					- ```shell
					  sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
					  Types: deb
					  URIs: https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/debian
					  Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
					  Components: stable
					  Signed-By: /etc/apt/keyrings/docker.asc
					  EOF
					  ```
			- 安装 Docker 核心组件
			  logseq.order-list-type:: number
				- ```shell
				  sudo apt update
				  sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
				  ```
				- > 包含了 [[docker-buildx]]与 [[docker-compose]]
		- ### [[Fedora]] / [[RHEL]] - [[yum]] / [[dnf]]
			- **1. 卸载旧版本**
				- ```
				  sudo dnf remove docker \
				                  docker-client \
				                  docker-client-latest \
				                  docker-common \
				                  docker-latest \
				                  docker-latest-logrotate \
				                  docker-logrotate \
				                  docker-selinux \
				                  docker-engine-selinux \
				                  docker-engine
				  ```
			- **2. 添加 Docker 官方软件源**
				- ```
				  sudo dnf config-manager addrepo --from-repofile https://download.docker.com/linux/fedora/docker-ce.repo
				  ```
			- **3. 安装 Docker Engine 及常用插件**
				- 安装社区版核心程序、命令行客户端、容器运行时以及 Compose 插件：
				- ```
				  sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
				  ```
				- > 包含了 [[docker-buildx]]与 [[docker-compose]]
			- **4. 启动 Docker 并设置开机自启**
				- ```
				  sudo systemctl enable --now docker
				  ```
	- ## 配置
		- ### 非**root**用户免 `sudo` 使用Docker
			- > 默认情况下只有 `root` 用户或 `sudo` 权限才能运行 Docker。若希望当前用户直接运行 `docker` 命令
			- 将当前用户加入 `docker` 用户组
				- ```shell
				  sudo usermod -aG docker $USER
				  ```
			- 刷新组权限（或重新登录终端使配置生效）
				- ```shell
				  newgrp docker
				  ```
			- 测试无 `sudo` 执行
				- ```shell
				  docker ps
				  ```