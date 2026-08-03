# 安装&初始化
	- ## 安装
		-
	- ## 初始化配置
		-
	- ## 卸载
		- ### 第一步：查看 Podman 是如何安装的
			- 执行以下命令检查安装来源：
			- **1. 检查二进制文件的具体路径**
				- ```bash
				  which podman
				  ```
				- **输出 `/usr/bin/podman`**：通常是通过系统的官方包管理器（`dnf` / `rpm` / `apt`）安装的。
				- **输出 `/usr/local/bin/podman` 或 `~/.local/bin/podman`**：通常是通过源码手动编译、二进制压缩包安装，或是 Python `pip` 安装。
				- **输出 `/var/lib/flatpak/...` 或含有 `flatpak` 路径**：是通过 Flatpak 安装的。
			- **2. 使用包管理器确认**
			  
			  在 **Fedora / RHEL / CentOS** 上执行：
				- ```bash
				  rpm -q podman
				  ```
				- 如果返回 `podman-x.x.x...`，说明是通过 RPM (DNF) 安装的。
			- 在 **Ubuntu / Debian** 上执行：
				- ```bash
				  dpkg -l | grep podman
				  ```
				- 如果有列表输出，说明是通过 `apt` 安装的。
			- 在 **Pip (Python)** 路径下查询（如果你还安装了 `podman-compose`）：
				- ```bash
				  pip list | grep podman
				  ```
		- ### 第二步：根据安装方式进行卸载
			- 在卸载前，建议先删除所有的容器、镜像和数据卷（可选）：
			- ```bash
			  podman system reset -f
			  ```
			- 选择对应的安装方式进行卸载：
			- #### 方式 1：通过系统的包管理器安装（最常见）
				- **Fedora / RHEL / CentOS：**
					- ```bash
					  sudo dnf remove podman podman-compose
					  ```
				- **Ubuntu / Debian：**
					- ```bash
					  sudo apt remove --purge podman podman-compose
					  ```
				- **Arch Linux：**
					- ```bash
					  sudo pacman -R podman
					  ```
				- #### 方式 2：通过 Python Pip 安装（通常指  `podman-compose` ）
					- 如果是通过 Python 环境安装的工具包：
					- ```bash
					  pip uninstall podman-compose
					  ```
				- #### 方式 3：通过 Flatpak 安装
					- ```bash
					  flatpak uninstall dev.podman.Podman
					  ```
				- #### 方式 4：手动二进制或源码安装
					- 如果是直接下载二进制文件解压到 `/usr/local/bin` 的，直接删除对应文件即可：
					- ```bash
					  sudo rm -f $(which podman)
					  ```
				- ### 第三步：清理剩余数据（可选）
					- 卸载软件后，相关的容器镜像和本地配置文件可能仍留在磁盘上，可以手动删除：
					- ```bash
					  # 删除当前用户的 Podman 配置和容器镜像数据
					  rm -rf ~/.local/share/containers/
					  rm -rf ~/.config/containers/
					  
					  # （如果是 root 运行过）删除全局数据
					  sudo rm -rf /var/lib/containers/
					  sudo rm -rf /etc/containers/
					  ```