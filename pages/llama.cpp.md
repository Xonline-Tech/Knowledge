category:: Software
website:: [Github](https://github.com/ggml-org/llama.cpp)

- # 安装
	- ## [[Fedora44]] / [[CUDA]] 安装
		- ```shell
		  # 准备编译环境
		  sudo dnf install git cmake gcc-c++ ninja-build
		  
		  # 前往软件包路径
		  
		  # 编译CUDA版本
		  git clone https://github.com/ggml-org/llama.cpp
		  cd llama.cpp
		  
		  cmake -B build \
		    -DGGML_CUDA=ON \
		    -DCMAKE_BUILD_TYPE=Release
		  
		  cmake --build build -j$(nproc)
		  ```
		- > **ERROR**
	- ## 在 [[Ubuntu24]] 环境中编译安装
		- 准备编译环境
		  logseq.order-list-type:: number
			- ```shell
			  sudo apt update
			  
			  sudo apt install -y \
			    git \
			    cmake \
			    ninja-build \
			    build-essential \
			    ccache \
			    libssl-dev \
			    libcurl4-openssl-dev
			  ```
			  #git #cmake #ninja-build #build-essential #ccache #libssl-dev #libcurl4-openssl-dev
		- 拉取 [llama.cpp源码](https://github.com/ggml-org/llama.cpp) 并进入路径
		  logseq.order-list-type:: number
			- ```shell
			  mkdir -p ~/src
			  cd ~/src
			  
			  git clone https://github.com/ggml-org/llama.cpp.git
			  cd llama.cpp
			  ```
		- 编译安装
		  logseq.order-list-type:: number
			- [[ROCm]] 环境安装
				- ```shell
				  cd ~/src/llama.cpp
				  
				  export ROCM_PATH=/opt/rocm/core-7.14
				  export PATH="$ROCM_PATH/bin:$ROCM_PATH/llvm/bin:$PATH"
				  export LD_LIBRARY_PATH="$ROCM_PATH/lib:${LD_LIBRARY_PATH:-}"
				  
				  cmake -S . -B build-hip -G Ninja \
				    -DGGML_HIP=ON \
				    -DGPU_TARGETS=gfx1100 \
				    -DCMAKE_BUILD_TYPE=Release \
				    -DCMAKE_PREFIX_PATH="$ROCM_PATH"
				    
				  cmake --build build-hip -j 8
				  
				  
				  ```
				- > **出现错误 does not contain the HIP runtime CMake package, expected at one hip-lang-xxx**
				  出现该问题主要是因为缺少 [[ROCm]] 开发包，需要安装 [[amdrocm-core-dev]]，然后清理缓存 `rm -rf build-hip` 后重新安装