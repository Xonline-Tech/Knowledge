alias:: xdna-driver
description:: 适用于Linux的AMD XDNA驱动（amdxdna.ko）和XRT SHIM库
website:: [Github](https://github.com/amd/xdna-driver)

- # 安装&初始化
	- ## 安装
		- > 官方要求系统
		  [[Ubuntu]] >= 22.04
		  [[Arch Linux]]
		  [[Fedora]] >= 44
		  Linux Kernel: v6.10 or above.
		- ### [[Fedora44]] 编译安装
			- #### 获取源码并准备环境
				- **获取源码**
				  logseq.order-list-type:: number
					- logseq.order-list-type:: number
					  ```shell
					  mkdir -p ~/.src
					  cd ~/.src
					  
					  git clone --recursive https://github.com/amd/xdna-driver.git
					  cd ~/.src/xdna-driver
					  ```
					- > **如果之前 clone 过**
					  ```shell
					  git pull
					  git submodule update --init --recursive
					  ```
				- **使用 [[toolbox]] 准备独立编译环境**
				  logseq.order-list-type:: number
					- > 如果安装 `toolbox` 先安装  
					  ```shell
					  sudo dnf install -y toolbox
					  ```
					- 创建`xrt-build`编译环境
					  logseq.order-list-type:: number
						- ```shell
						  toolbox create --release 44 xrt-build
						  ```
					- 进入环境
					  logseq.order-list-type:: number
						- ```shell
						  toolbox enter xrt-build
						  ```
					- 安装依赖
					  logseq.order-list-type:: number
						- ```shell
						  # 进入项目路径
						  cd ~/.src/xdna-driver
						  # 安装基础依赖
						  sudo dnf install -y \
						      gcc gcc-c++ cmake make git \
						      glibc-static libstdc++-static \
						      boost-devel boost-filesystem boost-program-options boost-static \
						      libdrm-devel \
						      libuuid-devel \
						      systemtap-sdt-devel \
						      rapidjson-devel \
						      openssl-devel \
						      protobuf-devel protobuf-compiler \
						      pybind11-devel python3-devel \
						      opencl-headers \
						      ocl-icd ocl-icd-devel \
						      rpm-build
						  
						  # 执行项目附带的依赖脚本
						  sudo ./tools/amdxdna_deps.sh
						  ```
				- **构建程序**
				  logseq.order-list-type:: number
					- logseq.order-list-type:: number
					  ```shell
					  cd ~/.src/xdna-driver/xrt/build
					  ./build.sh -npu -opt -disable-werror -j "$(nproc)"
					  ```
						- > 如果编译过程中报错，则修复错误后重新执行
						  ```shell
						  cd ~/.src/xdna-driver/xrt/build
						  rm -rf Release
						  ./build.sh -npu -opt -disable-werror -j "$(nproc)"
						  ```
				- **打包程序**
				  logseq.order-list-type:: number
					- logseq.order-list-type:: number
					  ```shell
					  # 
					  cd ~/.src/xdna-driver/xrt/build/Release
					  make package -j "$(nproc)"
					  
					  # 确认是否生成rpm包，应包含base、base-devel、npu
					  find ~/.src/xdna-driver/xrt/build/Release \
					    -type f -name '*.rpm' -printf '%p\n'
					  
					  ```
					- logseq.order-list-type:: number