category:: Software
website:: [官网](https://pytorch.org/)
description:: PyTorch 是一个以动态图和自动求导为核心、广泛用于深度学习模型开发与训练的开源 Python 框架。

- # 安装&初始化
	- ## 安装
		-
	- ## 初始化配置
		- ### 安装与配置结果测验
			- ```shell
			  python - <<'PY'
			  import torch
			  
			  print("PyTorch :", torch.__version__)
			  print("HIP     :", torch.version.hip)
			  print("CUDA API available:", torch.cuda.is_available())
			  print("GPU count:", torch.cuda.device_count())
			  
			  if torch.cuda.is_available():
			      print("GPU     :", torch.cuda.get_device_name(0))
			      p = torch.cuda.get_device_properties(0)
			      print("VRAM    : %.2f GiB" % (p.total_memory / 1024**3))
			  PY
			  ```
			- > **注意：**在AMD的GPU下`torch.cuda.is_available()`依旧是这么书写，且返回的是正常的结果，并不代表GPU为NVIDIA CUDA。
		- ### GPU 矩阵计算校验
			- ```shell
			  python - <<'PY'
			  import torch
			  import time
			  
			  device = "cuda"
			  
			  print("PyTorch:", torch.__version__)
			  print("HIP:", torch.version.hip)
			  print("GPU:", torch.cuda.get_device_name(0))
			  
			  n = 8192
			  
			  print(f"Creating {n}x{n} FP16 matrices...")
			  
			  a = torch.randn((n, n), device=device, dtype=torch.float16)
			  b = torch.randn((n, n), device=device, dtype=torch.float16)
			  
			  # warmup
			  for _ in range(3):
			      c = a @ b
			  
			  torch.cuda.synchronize()
			  
			  loops = 10
			  start = time.perf_counter()
			  
			  for _ in range(loops):
			      c = a @ b
			  
			  torch.cuda.synchronize()
			  elapsed = time.perf_counter() - start
			  
			  ops = 2 * n**3 * loops
			  tflops = ops / elapsed / 1e12
			  
			  print(f"Time: {elapsed:.3f} s")
			  print(f"Average: {elapsed / loops * 1000:.2f} ms")
			  print(f"Approx FP16 matmul: {tflops:.2f} TFLOPS")
			  
			  free, total = torch.cuda.mem_get_info()
			  print(f"VRAM free : {free / 1024**3:.2f} GiB")
			  print(f"VRAM total: {total / 1024**3:.2f} GiB")
			  
			  print("Result checksum:", c[0,0].item())
			  PY
			  ```
			- > **出现 `E-001h rocSHMEM Could not open libnuma. Returning`错误**
			  不用担心，这是一个ROCm7.14的[已知错误](https://rocm.docs.amd.com/en/docs-7.14.0/about/release-notes.html)。直接安装 [[libnuma]]来解决该问题。