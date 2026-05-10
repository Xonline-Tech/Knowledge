tags:: git,Github,ssh

- ### 生成 SSH 密钥
	- ```
	  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
	  ```
	  > 按照提示完成生成过程，默认情况下，密钥会保存在 `~/.ssh/id_rsa` 和 `~/.ssh/id_rsa.pub`。
- ### 将SSH 公钥添加到 GitHub
	- 复制公钥内容：
	  
	  ```
	  cat ~/.ssh/id_rsa.pub
	  ```
	- 打开 GitHub [SSH and GPG keys](https://github.com/settings/keys)，进入 `Settings` > `SSH and GPG keys` > `New SSH key`。
	- 将公钥粘贴进去并保存。
- ### 测试 SSH 连接
	- ```
	  ssh -T git@github.com
	  ```
-