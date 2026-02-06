category:: Notes

- ## 将笔记托管到Github
	- > 该步骤需要电脑中拥有git客户端或Git管理工具
	- **在笔记目录初始化git仓库（推荐）**
	  logseq.order-list-type:: number
		- **方式一：开启Logeq图谱的多版本控制功能，自动初始化Git仓库**
			- 可以在Logseq中打开上传的图谱，点击左上角菜单按钮，然后打开设置。选择多版本控制选项页，勾选**开启Git自动commit**后，应该会出现填写用户名与邮箱的弹出框，填写完成后会自动创建Git仓库。
			- ![image.png](../assets/image_1770271240880_0.png)
		- **方式二：使用命令行或GIt可视化工具手动创建**
			- > 这种方式无法获取Logseq的自动提交功能，需要手动commit
	- 初始化Github仓库，并push笔记仓库
	  logseq.order-list-type:: number
- ## 配置Github仓库
	- > 只有公开仓库才能享受免费的Github Pages发布功能
	- ### Action权限配置
		- 进入菜单 **Settings -> Actions->General->Workflow permissions**，选择**Read and write permissions**后点击**Save**保存。
		- ![image.png](../assets/image_1770280790194_0.png)
		-
-