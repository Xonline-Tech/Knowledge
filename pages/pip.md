category:: Software
website:: [官网](https://pypi.org/)
description:: `pip`是 Python 的包管理工具，用于从 PyPI 等仓库安装、升级和卸载第三方库。

-
- # 安装&初始化
	- ## 安装
		-
	- ## 初始化配置
		- ### 为PyPI配置镜像源
		  id:: 6a73dd27-a3ad-4be6-8043-1d412fe0eb84
			- #### [[清华大学开源软件镜像站]] - [PyPI帮助](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)
				- ```shell
				  # 升级 pip 到最新的版本
				  python -m pip install --upgrade pip
				  
				  # 配置源
				  pip config set global.index-url https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
				  ```