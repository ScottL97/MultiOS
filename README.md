# Description
A tool used to create a multiple OS boot disk automaticly and parallelly, also can be used to manage partitions of a bootable disk conveniently.
# 参数
## 模式
制作模式（刷ISO）：

* -m a：新创建分区刷ISO
* -m r：在某已存在分区刷ISO

维护模式（不刷ISO）：

* -m d：删除某系统分区
* -m i：删除所有分区，初始化U盘

## 目标磁盘设备名
-d 设备名：如-d /dev/sdb
## 目标磁盘分区号
-p 分区号：如-p 2（用于-m r和-m d）
## 系统映像文件路径
系统映像文件路径，-m a模式下支持多个：如/root/test.iso ./ubunto.iso
# 使用示例
```
$ ./multios-install -d /dev/sdb -m i # 清空磁盘分区，创建boot分区并初始化（安装grub2，复制文件）
$ ./multios-install -d /dev/sdb -m a test.iso # 创建一个新分区，刷test.iso系统映像
$ ./multios-install -d /dev/sdb -m a ubuntu.iso # 创建一个新分区，刷ubuntu.iso系统映像
$ ./multios-install -d /dev/sdb -m r -p 3 CentOS.iso # 在/dev/sdb3刷CentOS.iso系统映像，替换刚才刷的ubuntu.iso系统映像
$ ./multios-install -d /dev/sdb -m d -p 2 # 将/dev/sdb2分区删除，同时删除相应的配置
$ ./multios-install -d /dev/sdb -m a test2.iso test3.iso test5.iso # 支持并行
$ ./multios-install # 不输入-d参数（这时即使输入其他参数也无效）进入交互模式
```
