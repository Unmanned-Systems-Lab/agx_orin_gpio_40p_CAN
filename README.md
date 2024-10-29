 - 配置orin 的CAN总线，看库中的PDF文档，按照图片中所示接线
 - 下电操作
```bash
# 每次下电(关机)都需要重新输入。还没有写自动挂载的代码
sudo busybox devmem 0x0c303000 32 0x0000C400
sudo busybox devmem 0x0c303008 32 0x0000C458
sudo busybox devmem 0x0c303010 32 0x0000C400
sudo busybox devmem 0x0c303018 32 0x0000C458

sudo modprobe can
sudo modprobe can_raw
sudo modprobe mttcan

sudo ip link set down can0
sudo ip link set can0 type can bitrate 500000
sudo ip link set up can0
```
