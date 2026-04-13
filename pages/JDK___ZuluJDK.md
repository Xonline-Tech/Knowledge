alias:: ZuluJDK
website:: https://www.azul.com/

- # 安装&初始化
	- ## 安装
		- ###  [[MacOS]] - [[brew]]
			- ```shell
			  brew tap mdogan/zulu
			  brew install <name>
			  ```
		- ### [[Debian]] / [[Ubuntu]] - [[apt]]
			- ```shell
			  # 导入证书&添加源
			  sudo apt install -y gnupg ca-certificates curl
			  curl -s https://repos.azul.com/azul-repo.key \
			    | sudo gpg --dearmor -o /usr/share/keyrings/azul.gpg
			  echo "deb [signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main" \
			    | sudo tee /etc/apt/sources.list.d/zulu.list
			  sudo chmod 644 /usr/share/keyrings/azul.gpg
			  # 更新
			  sudo apt update
			  # 安装
			  sudo apt install zulu<jdk-version>-jdk
			  # For example
			  sudo apt install -y zulu21-jdk
			  ```
-