alias:: thu-ml/SageAttention
website:: [Github](https://github.com/thu-ml/SageAttention)

- /in
- # 安装&初始化
	- ## 安装
		- ### 仓库安装
			-
		- ### 源码编译安装
			- > 对于 CUDA>13.0&PyTorch>12.11的环境来说现仓库版本安装有问题，所以需要本地编译
			  执行命令前请先进入对应的Python虚拟环境
			- 如果已经安装其他版本请先卸载
				- ```shell
				  pip uninstall sageattention -y
				  # 确认卸载
				  pip list | grep sage
				  ```
			- 安装编译依赖
				- ```shell
				  pip install ninja packaging wheel setuptools
				  ```
			- 编译&安装
				- ```shell
				  cd /tmp
				  git clone https://github.com/thu-ml/SageAttention.git
				  cd SageAttention
				  NVCC_PREPEND_FLAGS="-allow-unsupported-compiler" pip install . --no-build-isolation
				  ```