category:: Services
website:: [Github](https://github.com/searxng/searxng) [官方文档](https://docs.searxng.org/index.html)
description:: SearXNG 是一个免费的互联网元搜索引擎，汇总了来自各种搜索服务和数据库的结果。用户既不被追踪，也不被画像。

- # 安装&初始化
	- ## 安装
		- ### 在 [[docker-compose]] 中运行
			- #### 从网络获取(推荐)
				- ```
				  # Create the environment and configuration directories
				  $ mkdir -p ./searxng/core-config/
				  $ cd ./searxng/
				  
				  # Fetch the latest compose template
				  $ curl -fsSL \
				      -O https://raw.githubusercontent.com/searxng/searxng/master/container/docker-compose.yml \
				      -O https://raw.githubusercontent.com/searxng/searxng/master/container/.env.example
				  ```
			- #### 手动创建
				- 创建compose文件 `vi docker-compose.yaml`
				  logseq.order-list-type:: number
				  collapsed:: true
					- ```yaml
					  # Read the documentation before using the `docker-compose.yml` file:
					  # https://docs.searxng.org/admin/installation-docker.html
					  
					  name: searxng
					  
					  services:
					    core:
					      container_name: searxng-core
					      image: docker.io/searxng/searxng:${SEARXNG_VERSION:-latest}
					      restart: always
					      ports:
					        - ${SEARXNG_HOST:+${SEARXNG_HOST}:}${SEARXNG_PORT:-8080}:${SEARXNG_PORT:-8080}
					      env_file: ./.env
					      volumes:
					        - ./core-config/:/etc/searxng/:Z
					        - core-data:/var/cache/searxng/
					  
					    valkey:
					      container_name: searxng-valkey
					      image: docker.io/valkey/valkey:9-alpine
					      command: valkey-server --save 30 1 --loglevel warning
					      restart: always
					      volumes:
					        - valkey-data:/data/
					  
					  volumes:
					    core-data:
					    valkey-data:
					  ```
				- 创建环境变量文件 `vi .env`
				  logseq.order-list-type:: number
				  collapsed:: true
					- ```
					  # Read the documentation before using the `docker-compose.yml` file:
					  # https://docs.searxng.org/admin/installation-docker.html
					  #
					  # Additional ENVs:
					  # https://docs.searxng.org/admin/settings/settings_general.html#settings-general
					  # https://docs.searxng.org/admin/settings/settings_server.html#settings-server
					  
					  # Use a specific version tag. E.g. "latest" or "2026.3.25-541c6c3cb".
					  #SEARXNG_VERSION=latest
					  
					  # Listen to a specific address.
					  #SEARXNG_HOST=[::]
					  
					  # Listen to a specific port.
					  #SEARXNG_PORT=8080
					  ```
				- logseq.order-list-type:: number
	- ## 初始化配置
		- ### 推荐配置
			- 编辑 `./core-config/settings.yml`
			  collapsed:: true
				- ```yaml
				  # SearXNG for OpenWebUI
				  # AI Search Optimized Configuration
				  
				  use_default_settings: true
				  
				  
				  general:
				  
				    # 搜索实例名称
				    instance_name: "AI Search"
				  
				    # 关闭调试
				    debug: false
				  
				  
				  search:
				  
				    # 关闭安全过滤
				    # AI搜索一般需要完整结果
				    safe_search: 0
				  
				    # 默认语言
				    default_lang: "zh-CN"
				  
				    # 自动补全关闭
				    # 避免额外请求
				    autocomplete: ""
				  
				    # OpenWebUI 必须开启 JSON
				    formats:
				      - html
				      - json
				  
				  
				  server:
				  
				    # 换成新的
				    secret_key: "替换成你的新key"
				  
				    # 图片代理
				    image_proxy: true
				  
				    # 个人使用关闭限流
				    limiter: false
				  
				    # 如果通过docker访问
				    bind_address: "0.0.0.0"
				  
				  
				  # Valkey缓存
				  # 你的docker-compose已有valkey
				  valkey:
				  
				    url: valkey://searxng-valkey:6379/0
				  
				  
				  
				  # 网络请求设置
				  outgoing:
				  
				    # 搜索超时
				    request_timeout: 5.0
				  
				    # 同时请求数量
				    max_request_timeout: 10.0
				  
				  
				  
				  # 引擎优化
				  engines:
				  
				    # 中文搜索
				    - name: baidu
				      disabled: false
				  
				    # 国际搜索
				    - name: bing
				      disabled: false
				  
				    - name: duckduckgo
				      disabled: false
				  
				  
				    # 技术搜索
				  
				    - name: github
				      disabled: false
				  
				    - name: wikipedia
				      disabled: false
				  
				  
				    # 删除不需要的
				    - name: ahmia
				      disabled: true
				  
				    - name: torch
				      disabled: true
				  ```