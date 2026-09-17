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
- # 使用
	- ## 参数设定
		- `-c` `--ctx-size` : 为模型上下文准备的 token 容量
		- `-ngl` `--n-gpu-layers` : 最多将多少层模型权重放到 GPU，可以用 `99` 数字表示放置99层，而不是 `99%`，因为模型达不到99层所以默认放入所有，在新版中甚至允许`all`参数表示放置所有。
		- `--device` : 指定llama.cpp使用哪块显卡进行推理，前提条件是通过 `HIP_VISIBLE_DEVICES` 允许 llama.cpp可以看见哪块显卡，才能通过`device`参数指定对应的显卡，如果存在多块显卡才会有后面的并行参数。
		- `-ctk` `--cache-type-k` : 对模型运行过程中产生的 `K/V Cache` 的进行量化，主要作用是用精度损失换取显存，llama.cpp 当前允许 KV 使用 f32、f16、bf16、q8_0、q4_0、q5 等多种格式。通常情况下推荐`k`、`v`设置相同的量化参数。
		- `-ctv` `--cache-type-v` : 同上
		- `-b` `--batch-size` : 逻辑上，一批最多处理多少 token
		- `-ub` `--ubatch-size` : 真正一次交给计算图/GPU处理多少 token
		- `--flash-attn` : `on/off`，改变计算顺序，把 Attention 分块计算，并尽量让中间数据留在 GPU 高速片上存储，而不是频繁读写显存。
		- ### MTP
			- `-md` :
			- `--spec-type` :