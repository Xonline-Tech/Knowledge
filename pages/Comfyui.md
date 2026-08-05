- [[pip]]
- 为 **Comfyui**创建一个专属路径用来装**Python环境与软件**本身。
	- > 在此建议，如果你的Linux环境挂载了**NTFS驱动器**，那么建议你将尽量将Python环境与软件安装在 `ext`或 `btrfs`分区，模型等文件可以放在 `NTFS`分区中。
	- ```bash
	  mkdir -p ~/.local/share/comfyui
	  cd ~/.local/share/comfyui
	  ```
- 进入为Comfyui准备的工作路径，创建虚拟环境
	- ```shell
	  python3.12 -m venv comfyui-env
	  # 进入环境
	  source comfyui-env/bin/activate
	  
	  # 升级pip
	  python -m pip install --upgrade pip setuptools wheel
	  ```
- 克隆 Comfyui仓库
	- ```bash
	  git clone https://github.com/comfyanonymous/ComfyUI.git
	  cd ComfyUI
	  ```
- 安装 [[PyTorch]]（stable-2.13.0/CUDA-13.0）
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
- ```bash
  pip install -r requirements.txt
  ```
- 然后安装几个常用组件：
- ```
  pip install xformers accelerate sentencepiece einops safetensors
  ```
- # 第六步：启动 ComfyUI
  
  第一次启动：
  
  ```
  python main.py
  ```
  
  如果局域网访问：
  
  ```
  python main.py --listen 0.0.0.0
  ```
  
  浏览器打开：
  
  ```
  http://127.0.0.1:8188
  ```
  
  ---
- # 第七步：安装 ComfyUI Manager
  
  ```
  cd custom_nodes
  
  git clone https://github.com/ltdrdata/ComfyUI-Manager.git
  
  cd ..
  ```
  
  重启 ComfyUI。
  
  之后网页右上角应该会出现 **Manager**。