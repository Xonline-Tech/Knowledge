category:: Notes

- ## 克隆项目与配置
	- ```shell
	  git clone https://gitee.com/neilpang/acme.sh.git
	  cd acme.sh/
	  sh ./acme.sh --install -m <E-Mail>
	  ```
		- **E-Mail:**用户邮箱
- ## 检查Token与域ID
	- ### 创建令牌
		- ![image.png](../assets/image_1776935454598_0.png)
		- ![image.png](../assets/image_1776935713015_0.png)
- ## 申请证书
	- ```shell
	  # 1. 设置 Cloudflare 令牌环境变量
	  export CF_Token=""
	  
	  # CF_Zone_ID、CF_Account_ID在对应域的主页下
	  export CF_Zone_ID=""
	  export CF_Account_ID=""
	  
	  # 2. 申请证书（包含根域名和所有二级子域名）
	  ~/.acme.sh/acme.sh --issue --dns dns_cf -d <主域名> -d *.sunyard.team
	  ```
- **主域名：**：DNS解析的主域名
- **泛域名：***.xon.ink