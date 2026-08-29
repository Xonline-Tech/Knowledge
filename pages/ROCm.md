# 安装&初始化
	- ## 安装
		- > 优先参考 [官方指南](https://rocm.docs.amd.com/en/docs-7.14.0/install/rocm.html)
		- ### [[Ubuntu24]] 安装
			- 确定内核版本与ROCm矩阵版本相同 [官方文档](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html)
			  logseq.order-list-type:: number
				- ```shell
				  uname -r
				  cat /etc/os-release | grep -E 'PRETTY_NAME|VERSION_ID'
				  ```
				- > ROCm 7.14 对 Radeon + Ubuntu 24.04.4 官方矩阵列出的内核是 GA `6.8`。
			- 安装基础依赖
			  logseq.order-list-type:: number
				- ```shell
				  sudo apt update
				  
				  sudo apt install -y \
				      wget \
				      gpg \
				      linux-headers-$(uname -r) \
				      linux-modules-extra-$(uname -r) \
				      libatomic1 \
				      libquadmath0
				  ```
			- 确认用户GPU权限
			  logseq.order-list-type:: number
				- ```shell
				  groups
				  ```
					- 最好包含`video`、`render`，如果没有则执行命令添加，并**重新登录**
						- ```shell
						  sudo usermod -aG video,render $USER
						  ```
			- 安装`amdgpu-install`
			  logseq.order-list-type:: number
				- ```shell
				  wget https://repo.radeon.com/amdgpu-install/31.40.1/ubuntu/noble/amdgpu-install_31.40.1.314001-1_all.deb
				  sudo apt install ./amdgpu-install_31.40.1.314001-1_all.deb
				  ```
			- 检查`amdgpu-install`版本与可安装内容并安装
			  logseq.order-list-type:: number
				- 刷新缓存
				  logseq.order-list-type:: number
					- ```
					  sudo apt update
					  ```
					  因为刚安装的 `amdgpu-install` 会加入 AMD 官方软件仓库，必须先刷新一次软件索引。
				- 确认 installer：
				  logseq.order-list-type:: number
					- ```
					  amdgpu-install --version
					  ```
					- 以及：
					- ```
					  sudo amdgpu-install --list-usecase
					  ```
					- 应该能看到：
						- ```
						  graphics
						  rocm
						  dkms
						  ...
						  ```
				- 确认无误后，开始安装
				  logseq.order-list-type:: number
					- ```shell
					  sudo amdgpu-install -y --usecase=rocm,graphics --gfxversion=auto
					  ```
				- 安装结束后重启
				  logseq.order-list-type:: number
					- ```shell
					  sudo reboot
					  ```
				- 检查状态（仅供参考）
				  logseq.order-list-type:: number
					- ```shell
					  $ uname -r
					  6.8.0-138-generic
					  
					  $ lspci -nnk -s 01:00.0
					  01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Navi 31 [Radeon RX 7900 XT/7900 XTX/7900M] [1002:744c] (rev c8)
					          Subsystem: Gigabyte Technology Co., Ltd Navi 31 [Radeon RX 7900 XT/7900 XTX] [1458:240e]
					          Kernel driver in use: amdgpu
					          Kernel modules: amdgpu
					          
					  $ ls -l /dev/kfd
					  crw-rw---- 1 root render 236, 0 Aug 29 12:54 /dev/kfd
					  
					  $ ls -l /dev/dri/renderD*
					  crw-rw---- 1 root render 226, 128 Aug 29 12:54 /dev/dri/renderD128
					  
					  $ dkms status
					  amdgpu/6.19.14-2377056.24.04, 6.8.0-138-generic, x86_64: installed
					  
					  $ rocminfo | grep -E 'Name:|Marketing Name:' | head -30
					    Name:                    AMD Ryzen 7 5700X 8-Core Processor 
					    Marketing Name:          AMD Ryzen 7 5700X 8-Core Processor 
					    Vendor Name:             CPU                                
					    Name:                    gfx1100                            
					    Marketing Name:          AMD Radeon RX 7900 XTX             
					    Vendor Name:             AMD                                
					        Name:                    amdgcn-amd-amdhsa--gfx1100         
					        Name:                    amdgcn-amd-amdhsa--gfx11-generic   
					  
					  $ amd-smi list
					  GPU: 0
					      BDF: 0000:01:00.0
					      UUID: 7100744c-0000-1000-8014-cfa91e2d70bd
					      KFD_ID: 58965
					      NODE_ID: 1
					      PARTITION_ID: 0
					  
					  ```