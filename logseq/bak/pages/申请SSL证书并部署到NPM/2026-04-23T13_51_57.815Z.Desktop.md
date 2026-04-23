- ```shell
  git clone https://gitee.com/neilpang/acme.sh.git
  cd acme.sh/
  sh ./acme.sh --install -m shih.zhang@sunyard.com
  
  # 2. 设置 Cloudflare 令牌环境变量
  export CF_Token=""
  
  # CF_Zone_ID、CF_Account_ID在对应域的主页下
  export CF_Zone_ID=""
  export CF_Account_ID=""
  
  # 3. 申请证书（包含根域名和所有二级子域名）
  ~/.acme.sh/acme.sh --issue --dns dns_cf -d sunyard.team -d *.sunyard.team
  ```