alias:: 达芬奇
category:: Software
type:: 影音💿

- /
- # 安装&初始化
	- ## 安装
		- ### [[Fedora]] / [[RHEL]] - [[yum]] / [[dnf]]
			- 确认环境配置
			  logseq.order-list-type:: number
				- ```shell
				  cat /etc/fedora-release
				  lspci -nnk | grep -EA3 'VGA|Display'
				  ```
				- 正常应该看到 `Kernel driver in use: amdgpu`
				- > **不要安装 AMDGPU-PRO 显卡内核驱动。** Fedora 官方 ROCm 文档明确说 Fedora 环境不需要 AMDGPU-PRO 驱动，直接使用内核自带 `amdgpu`。
			- 安装依赖
			  logseq.order-list-type:: number
				- ```shell
				  sudo dnf install rocm rocm-opencl rocm-clinfo
				  ```
				  #ROCm #rocm-opencl #rocm-clinfo
			- 把自己加入 GPU 权限组
			  logseq.order-list-type:: number
				- ```shell
				  sudo usermod -aG render,video $USER
				  ```
				  注销再登录，或者直接重启
				  ```shell
				  reboot
				  ```
			- 测试环境配置
			  logseq.order-list-type:: number
				- ```shell
				  rocminfo
				  rocm-clinfo
				  ```
				- 输出示例
					- ```shell
					  $ rocminfo
					  Name: gfx1103
					  Marketing Name: AMD Radeon 780M Graphics
					  
					  $ rocm-clinfo
					  Platform Name: AMD Accelerated Parallel Processing
					  Device Type: CL_DEVICE_TYPE_GPU
					  ```