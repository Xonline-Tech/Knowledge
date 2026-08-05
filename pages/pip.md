category:: Software

-
- # 安装&初始化
	- ## 安装
		-
	- ## 初始化配置
		- ### 配置镜像源
			- #### [[清华大学开源软件镜像站]] - [PyPI帮助](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)
				- ```shell
				  # 升级 pip 到最新的版本
				  python -m pip install --upgrade pip
				  
				  # 配置源
				  pip config set global.index-url https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
				  ```