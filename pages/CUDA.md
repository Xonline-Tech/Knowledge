# 安装&初始化
	- ## 安装
		- ### [[Fedora]] / [[RHEL]] - [[yum]] / [[dnf]]
			- 先确认显卡：
			  logseq.order-list-type:: number
				- ```bash
				  lspci | grep -i nvidia
				  ```
			- 安装依赖：
			  logseq.order-list-type:: number
				- ```bash
				  sudo dnf install -y \
				  kernel-devel \
				  kernel-headers \
				  gcc \
				  gcc-c++ \
				  make \
				  git \
				  wget \
				  curl
				  ```
			- 添加 CUDA 13 仓库
			  logseq.order-list-type:: number
				- ```bash
				  sudo dnf config-manager addrepo \
				  --from-repofile=https://developer.download.nvidia.com/compute/cuda/repos/fedora44/x86_64/cuda-fedora44.repo
				  ```
				- 刷新：
				- ```
				  sudo dnf clean all
				  sudo dnf makecache
				  ```
			- 安装 CUDA 工具集
			  logseq.order-list-type:: number
				- ```bash
				  sudo dnf install -y cuda-toolkit-13
				  ```
				- > 检查`nvcc`是否可用，如果不可用执行如下命令
					- ```shell
					  echo 'export CUDA_HOME=/usr/local/cuda-13.3' >> ~/.bashrc
					  echo 'export PATH=$CUDA_HOME/bin:$PATH' >> ~/.bashrc
					  echo 'export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
					  source ~/.bashrc
					  ```
			- 安装CUDA驱动
			  logseq.order-list-type:: number
				- 已经安装了 [[RPMFusion]]的NVIDIA驱动
				  logseq.order-list-type:: number
					-
				- 安装NVIDIA 官方 CUDA 仓库驱动
				  logseq.order-list-type:: number
					- **如果已经安装了 [[RPMFusion]]的NVIDIA驱动请先卸载**
						- 卸载 `nvidia` 驱动
							- ```shell
							  sudo dnf remove \
							  akmod-nvidia \
							  xorg-x11-drv-nvidia\*
							  ```
							- > **请注意：**不要删除`cuda*`的包，如果提示可以执行
							  ```shell
							  sudo dnf remove \
							  'akmod-nvidia*' \
							  'xorg-x11-drv-nvidia*'
							  ```
						- 清理缓存
							- ```shell
							  sudo dnf clean all
							  sudo dnf autoremove -y
							  ```
						- 确认 RPM Fusion驱动已经不存在
							- ```shell
							  rpm -qa | grep nvidia
							  ```
	-
	-
	-
	- ## 初始化配置
		-