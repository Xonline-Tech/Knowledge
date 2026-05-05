alias:: icloudpd-web
category:: Services
description:: iCloudPD-Web 是带有网页客户端的[[iCloud Photos Downloader]]的GUI包装器。
website:: [Github](https://github.com/AirswitchAsa/icloudpd-web) [Docker Image](https://hub.docker.com/r/spicadust/icloudpd-web)

-
- # 安装&初始化
	- ## 安装
		- ### 在 [[docker-compose]] 中运行
			- ```yaml
			  version: "3.8"
			  services:
			    app:
			      image: spicadust/icloudpd-web:latest
			      container_name: icloudpd-web
			      ports:
			        - "5000:5000"  # Web UI 默认端口 5000
			      environment:
			        - HOST=0.0.0.0
			        - PORT=5000
			        # 可选：禁止密码（开发/本地情况下）
			        - NO_PASSWORD=true
			        # 如果需要允许跨域
			        - ALLOWED_ORIGINS=*
			        # 指定 Session/cookie 保存目录
			        - COOKIE_DIRECTORY=/data/cookies
			      volumes:
			        - ./data:/data
			        - ./config:/policies
			        # 照片备份指定路径，宿主机与容器内均非固定，可在webui配置
			        - ./Photos:/Photos
			  ```
	- ## 初始化配置