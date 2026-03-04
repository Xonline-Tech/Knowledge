category:: Notes
tags:: Swap,zram

- # 开始
- 因为我使用的是[[Fedora]]，默认启用了[[zram]]，所以暂时跳过安装步骤
- # 修改配置 
  
  ```
  sudo nano /usr/lib/systemd/zram-generator.conf
  # 或者也可以添加/etc/systemd/zram-generator.conf配置文件，优先级大于上面的
  
  [zram0]
  # zram-size = min(ram / 2, 4096) # default
  # 以下是几个实例 配置一个就可
  zram-size = ram * 2
  zram-size = ram * 0.75
  
  # compression-algorithm 常用 zstd（压缩率高）或 lzo（速度快）。
  compression-algorithm = zstd
  ```