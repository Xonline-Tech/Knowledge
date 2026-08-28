category:: Software
website:: [官网](https://comfy.org/zh-CN/) [Github](https://github.com/Comfy-Org/ComfyUI)
description:: Comfy 是面向专业视觉人士的 AI 创作引擎。您可以精确掌控每个模型、每个参数和每个输出。

- # 安装&初始化
	- ## 安装
		- ### 前置完成步骤
			- 完成 [[CUDA]] 驱动与相关工具的安装
			- 保持系统与 [[Python]]环境为最新
			  collapsed:: true
				- #### Fedora系统命令参考
					- ```shell
					  # 更新系统
					  sudo dnf upgrade --refresh -y
					  sudo reboot
					  
					  # 安装基础工具
					  sudo dnf install -y \
					  git wget curl vim unzip \
					  gcc gcc-c++ make \
					  kernel-devel kernel-headers \
					  python3.12 python3.12-devel \
					  cmake ninja-build
					  ```
					-
			- *(可选) 为 [[pip]]* ((6a73dd27-a3ad-4be6-8043-1d412fe0eb84))
		- ### 开始安装
			- 为 **Comfyui**创建一个专属路径用来装**Python环境与软件**本身。
			  logseq.order-list-type:: number
				- > 在此建议，如果你的Linux环境挂载了**NTFS驱动器**，那么建议你将尽量将Python环境与软件安装在 `ext`或 `btrfs`分区，模型等文件可以放在 `NTFS`分区中。
				- ```bash
				  mkdir -p ~/.local/share/comfyui
				  cd ~/.local/share/comfyui
				  ```
			- 进入为Comfyui准备的工作路径，创建虚拟环境
			  logseq.order-list-type:: number
				- ```shell
				  python3.12 -m venv comfyui-env
				  # 进入环境
				  source comfyui-env/bin/activate
				  
				  # 升级pip
				  python -m pip install --upgrade pip setuptools wheel
				  ```
			- 克隆 Comfyui仓库
			  logseq.order-list-type:: number
				- ```bash
				  git clone https://github.com/comfyanonymous/ComfyUI.git
				  cd ComfyUI
				  ```
			- 安装 [[PyTorch]]（stable-2.13.0/CUDA-13.0）
			  logseq.order-list-type:: number
				- ```shell
				  pip3 install torch torchvision torchaudio
				  ```
				- 验证 PyTorch
					- 执行：
						- ```bash
						  python
						  ```
					- 输入：
						- ```python
						  import torch
						  - print(torch.__version__)
						  print(torch.version.cuda)
						  print(torch.cuda.is_available())
						  print(torch.cuda.get_device_name(0))
						  ```
					- 应该看到类似：
						- ```
						  2.13.0+cu132
						  13.2
						  True
						  NVIDIA GeForce RTX 4060
						  ```
					- 如果 `torch.cuda.is_available()` 返回 `True`，说明 GPU 推理环境已经准备好了。
			- 安装 ComfyUI 依赖
			  logseq.order-list-type:: number
				- ```bash
				  pip install -r requirements.txt
				  ```
			- 然后安装几个常用组件：
			  logseq.order-list-type:: number
				- ```bash
				  # 针对xformers对cuda13的单独处理，其他情况参考官网或点击代码下方标签
				  pip install -U xformers --index-url https://download.pytorch.org/whl/cu130
				  pip install accelerate einops safetensors
				  ```
				  #xformers
		- ### 启动
			- ```shell
			  # 如果是本机访问
			  python main.py
			  
			  # 局域网访问
			  python main.py --listen 0.0.0.0
			  ```
	- ## 初始化配置
		-
- > 接下来
	- #### 插件
		- 安装 [[SageAttention]]
		- 安装 [[ComfyUI Manager]]