category:: plugins
upstream:: [[ComfyUI]]
website:: [Github](https://github.com/facebookresearch/xformers) [官网](https://facebookresearch.github.io/xformers/)

- # 安装&初始化
	- ## 安装
		- > **(RECOMMENDED, linux & win) Install latest stable with pip**: Requires [PyTorch 2.10.0](https://pytorch.org/get-started/locally/)
		- ```bash
		  # [linux & win] cuda 12.6 version
		  pip3 install -U xformers --index-url https://download.pytorch.org/whl/cu126
		  # [linux & win] cuda 12.8 version
		  pip3 install -U xformers --index-url https://download.pytorch.org/whl/cu128
		  # [linux & win] cuda 13.0 version
		  pip3 install -U xformers --index-url https://download.pytorch.org/whl/cu130
		  # [linux only] (EXPERIMENTAL) rocm 7.1 version
		  pip3 install -U xformers --index-url https://download.pytorch.org/whl/rocm7.1
		  ```