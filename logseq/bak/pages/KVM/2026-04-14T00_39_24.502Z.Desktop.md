category:: Software
website:: https://linux-kvm.org/page/Main_Page

- # 安装&初始化
	- ## 安装
		- ### 在[[Fedora]]中安装
			- Fedora社区已经整理好了部署虚拟化套件所需要的Group包，所以部署起来极其简单
			- 接下来安装服务并启动
				- ```shell
				  # 运行以下命令以在虚拟化组中安装强制包和默认包
				  sudo dnf install @virtualization
				  # 安装后,启动libvirtd服务
				  sudo systemctl start libvirtd
				  # 启动服务,请运行
				  sudo systemctl enable libvirtd
				  # 验证服务状态
				  sudo systemctl status libvirtd
				  ```
			- 验证KVM内核是否正确加载
				- ```shell
				  $ lsmod | grep kvm
				  kvm_amd               114688  0
				  kvm                   831488  1 kvm_amd
				  ```
			- 为当前用户配置权限
				- ```shell
				  sudo usermod -aG libvirt $(whoami)
				  newgrp libvirt
				  ```
			- collapsed:: true
			  > 额外信息
				- **Virtualization****Base Group**包信息
					- collapsed:: true
					  ```shell
					  $ dnf group info virtualization
					  
					  Group: Virtualization
					   Description: These packages provide a graphical virtualization environment.
					   Mandatory Packages:
					     virt-install
					   Default Packages:
					     libvirt-daemon-config-network
					     libvirt-daemon-kvm
					     qemu-kvm
					     virt-manager
					     virt-viewer
					   Optional Packages:
					     libguestfs-tools
					     python3-libguestfs
					     virt-top
					  ```
						- [[qemu-kvm]]
						- [[virt-manager]]
						- [[virt-viewer]]
						- [[virt-top]]
						-
				- 🔗参考链接
					- https://docs.fedoraproject.org/en-US/quick-docs/virtualization-getting-started/