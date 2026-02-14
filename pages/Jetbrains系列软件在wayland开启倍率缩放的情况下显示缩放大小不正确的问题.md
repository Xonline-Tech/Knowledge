- 在 [[Wayland]] 环境中，在在修改缩放倍率后，软件显示缩放不正确，导致显示内容变大。
- # 解决方案
	- ## 通用方案
		- 在启动参数中添加如下参数
		- ```
		  -Dawt.toolkit.name=WLToolkit
		  ```
	- [[KDE]]方案
		- ![](http://docmost.sunyard.team:9945/api/files/019ae2fd-3289-72a1-8774-eb93a0ad92f5/image.png)