# 安装
	- ## 在 [[Ubuntu24]] 编译安装
		- 如果已经安装，先卸载旧版本
			- ```shell
			  sudo apt remove -y btop
			  ```
		- 如果是A卡，确认
			- ```shell
			  ldconfig -p | grep librocm_smi64
			  
			  find /opt/rocm -name 'librocm_smi64.so*' 2>/dev/null
			  ```
			- 是否能找到 `/opt/rocm/lib/librocm_smi64.so`
		- 安装编译所需依赖
			- ```shell
			  sudo apt update
			  sudo apt install -y \
			      gcc-14 \
			      g++-14 \
			      git \
			      make \
			      coreutils \
			      sed \
			      lowdown
			  ```
		- 创建路径并获取源码
			- ```shell
			  mkdir -p ~/src
			  cd ~/src
			  
			  git clone https://github.com/aristocratos/btop.git
			  cd btop
			  ```
		- 编译并指定显卡支持
			- ```shell
			  make clean
			  
			  make \
			      CXX=g++-14 \
			      GPU_SUPPORT=true \
			      -j"$(nproc)"
			  ```
		- 检查编译是否如预期
			- ```shell
			  # 检查版本
			  ./bin/btop --version
			  ```
				- > **预期结果**
				  btop version: 1.4.7
				  Compiled with: g++-14 ...
				  Configured with: make STATIC= **GPU_SUPPORT=true** RSMI_STATIC=
			- ```shell
			  # 运行测试
			  ./bin/btop
			  ```
		- 安装编译版本
			- ```shell
			  sudo make install
			  hash -r
			  ```