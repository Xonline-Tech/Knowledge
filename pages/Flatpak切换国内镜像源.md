- > 为 [[Flatpak]] 切换国内镜像源
- 选择合适的国内镜像源并执行以下命令：
	- **中科大镜像**：
	  
	  ```
	  flatpak remote-modify flathub --url=https://mirrors.ustc.edu.cn/flathub
	  ```
	- **上海交大镜像**：
	  
	  ```
	  flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
	  ```
- 验证配置
  
  查看当前仓库配置，确保已成功切换到国内源：
	- ```
	  flatpak remotes --show-details
	  ```