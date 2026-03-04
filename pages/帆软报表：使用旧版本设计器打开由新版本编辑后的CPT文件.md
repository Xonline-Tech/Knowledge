category:: Notes
tags:: 帆软报表

- 使用记事本打开CPT文件，修改以下对应行
	- ### 修改releaseVersion版本
		- 修改前
			- ```xml
			  <WorkBook xmlVersion="20211223" releaseVersion="11.0.0">
			  ```
			- > **releaseVersion:** 高版本ID
		- 修改后
			- ```xml
			  <WorkBook xmlVersion="20211223" releaseVersion="8.0.0">
			  ```
			- > **releaseVersion:** 低版本ID
	- ### 删除DesignerVersion标签
		- ```xml
		  <DesignerVersion DesignerVersion="LAA"/>
		  ```