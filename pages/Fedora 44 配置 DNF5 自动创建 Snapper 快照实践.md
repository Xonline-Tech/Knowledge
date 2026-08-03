## 前提条件

确认根分区使用 Btrfs：

```
findmnt /
```

安装 Snapper：

```
sudo dnf install snapper
```

初始化 Snapper 配置：

```
sudo snapper -c root create-config /
```

验证配置：

```
snapper list-configs
```

应看到：

```
root
```

---
- ## 创建 DNF5 Actions 配置
  
  创建目录：
  
  ```
  sudo mkdir -p /etc/dnf/libdnf5-plugins/actions.d
  ```
  
  创建配置文件：
  
  ```
  sudo nano /etc/dnf/libdnf5-plugins/actions.d/snapper.actions
  ```
  
  写入以下内容：
  
  ```
  # Get snapshot description
  pre_transaction::::/usr/bin/sh -c echo\ "tmp.cmd=$(ps\ -o\ command\ --no-headers\ -p\ '${pid}')"
  
  # Create pre snapshot
  pre_transaction::::/usr/bin/sh -c echo\ "tmp.snapper_pre_number=$(snapper\ create\ -c\ number\ -t\ pre\ -p\ -d\ '${tmp.cmd}')"
  
  # Create post snapshot
  post_transaction::::/usr/bin/sh -c [\ -n\ "${tmp.snapper_pre_number}"\ ]\ &&\ snapper\ create\ -c\ number\ -t\ post\ --pre-number\ "${tmp.snapper_pre_number}"\ -d\ "${tmp.cmd}"\ ;\ echo\ tmp.snapper_pre_number\ ;\ echo\ tmp.cmd
  ```
  
  > 
  
  **注意：** `actions` 插件中的 Shell 命令需要对空格进行转义（`\ `），否则命令会被错误拆分，导致执行失败。
  
  ---
- ## 测试
  
  安装一个软件包：
  
  ```
  sudo dnf install htop
  ```
  
  或重新安装：
  
  ```
  sudo dnf reinstall htop
  ```
  
  查看快照：
  
  ```
  snapper list
  ```
  
  正常情况下会生成一组事务快照：
  
  ```
  # | Type | Pre # | Description
  1 | pre  |       | dnf install ...
  2 | post | 1     | dnf install ...
  ```
  
  ---
- ## 常见问题
- ### 执行事务时报错
  
  ```
  unexpected EOF while looking for matching ')'
  ```
  
  **原因：**
  
  `snapper.actions` 中的 Shell 命令没有对空格进行转义，导致 `actions` 插件解析失败。
  
  **解决方法：**
  
  使用本文提供的完整配置文件，确保所有需要的空格均使用 `\` 进行转义。
  
  ---
- ### 未生成任何快照
  
  执行：
  
  ```
  sudo snapper create -d test
  ```
  
  若该命令也无法创建快照，则问题通常出在 Snapper 本身，而不是 DNF Hook。建议进一步检查：
- Snapper 配置是否正确；
- `.snapshots` 子卷是否存在；
- Btrfs 子卷结构是否符合 Snapper 要求；
- Snapper 配置文件权限及 ACL 是否正确。
  
  ---
- ## 建议
  
  为了获得类似 openSUSE 的系统回滚体验，建议同时配置以下组件：
- Snapper（快照管理）
- libdnf5-plugin-actions（DNF5 自动快照）
- grub-btrfs（启动菜单自动识别快照）
- Btrfs Assistant（图形化管理 Snapper）
  
  完成上述配置后，每次 DNF 软件包事务都会自动创建事务前（Pre）和事务后（Post）快照，便于在升级失败或软件异常时快速回滚系统。