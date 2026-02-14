tags:: alpine,docker,docker-compose

- # 确认安装源是否已经启用
	- 确认 `community` 源已经被启用
		- ```
		  vi /etc/apk/repositories
		  ```
	- 检查 `community` 是否被注释或缺失，如果没有则添加
		- ```
		  http://mirrors.ustc.edu.cn/alpine/v3.23/community
		  ```
	- > 也可以添加别的community
	- 然后执行
		- ```
		  apk update
		  ```
- # 安装 [[docker]] 与 [[docker-compose]]
	- ```
	  apk add docker docker-cli-compose
	  ```
- # 开启自启动
	- ```
	  rc-update add docker boot
	  service docker start
	  ```
- # 确认版本
	- ```
	  docker version
	  docker compose version
	  ```