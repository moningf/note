```
sudo pacman -S qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat
sudo systemctl enable --now libvirtd
sudo usermod -aG libvirt $(whoami)
```
```
virt-manager
```
```
sudo pacman -S qemu-full virt-manager
```

查看当前网络状态
`virsh net-list --all`


你会看到类似：

 Name                 State      Autostart   Persistent
-------------------------------------------------------
 default              inactive   yes         yes


inactive → 网络没启动

2️⃣ 激活默认网络
```
sudo virsh net-start default
```

然后设置开机自动启动：
```
sudo virsh net-autostart default
```



再次检查：
```
virsh net-list --all
```



State 应该变成 active