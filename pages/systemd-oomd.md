category:: Software
type:: 系统⚙️
description:: systemd-oomd 是 [[systemd]] 提供的一个用户空间的内存压力监控和进程终止守护进程，用来防止系统因内存耗尽而变得不稳定。它通过监控内存和交换区的使用情况，当检测到内存压力达到阈值时，优先杀掉内存占用高且优先级较低的进程，从而保护系统整体稳定性。

- # 安装&初始化
	- ## 安装
		-
	- ## 初始化配置
		- ```shell
		  sudo nano /etc/systemd/system/user.slice.d/oomd.conf
		  sudo systemctl daemon-reload
		  sudo systemctl restart systemd-oomd
		  # ！！！执行下方命令会重启所有程序，包括系统桌面，所以建议执行完上面三部直接重启电脑更加彻底
		  sudo systemctl restart user.slice
		  ```