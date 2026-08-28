category:: Software
website:: [Github](https://github.com/ggml-org/llama.cpp)

- # 安装&初始化
	- ## 安装
		- ### [[Fedora44]] / [[CUDA]] 安装
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