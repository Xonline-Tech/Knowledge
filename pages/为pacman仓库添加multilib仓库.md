- 开启`multilib` 仓库
  logseq.order-list-type:: number
	- ```
	  sudo vim /etc/pacman.conf
	  
	  # 放开multilib仓库注释
	  [multilib]
	  Include = /etc/pacman.d/mirrorlist
	  ```
- 刷新pacman缓存
  logseq.order-list-type:: number
	- ```
	  sudo pacman -Syy
	  ```