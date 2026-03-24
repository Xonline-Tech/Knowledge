alias:: svn

- # 安装&初始化
	- ## 安装
		- ### [[Fedora]] / [[RHEL]] - [[yum]] / [[dnf]]
			- ```shell
			  # 使用 yum 安装
			  yum install subversion
			  
			  # 使用 dnf 安装
			  dnf install subversion
			  ```
	- ## 初始化配置
		-
- # 使用
	- 保留路径导出单次提交记录
		- ```shell
		  REV=1234; SVN_URL="https://svn.xxx.com/project/trunk"; OUT="export_$REV"; mkdir -p "$OUT"; svn diff --summarize -c "$REV" "$SVN_URL" | awk '$1!="D"{print $2}' | while read -r f; do rel="${f#$SVN_URL/}"; mkdir -p "$OUT/$(dirname "$rel")"; svn export -r "$REV" "$f" "$OUT/$rel" --force > /dev/null; done
		  ```
			- `REV` : 版本号
			- `SVN_URL` : 完整路径
- # 下一步
	- ## 安装可视化管理工具
		- [[kdesvn]]