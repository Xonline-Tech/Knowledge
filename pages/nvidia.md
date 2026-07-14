- ```
  /sbin/lspci | grep -e VGA 
     13  [ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy BIOS mode"
     14  sudo dnf install mokutil
     15  mokutil --sb-state
     16  sudo dnf install akmod-nvidia
     17  sudo dnf install xorg-x11-drv-nvidia-cuda 
     18  modinfo -F version nvidia
     19  sudo dnf install xorg-x11-drv-nvidia-cuda-libs
     20  dnf list --installed | grep nvidia
     21  systemctl reboot
  
  ```