# TX2系统备份、烧制以及修改

本帖设计到系统备份以及如何修改备份镜像的操作，具体如下：

### 1、系统备份

首先安装好对应版本的瑞泰官方烧制系统工具，在运行完`sudo ./install.sh`以后得到成功提示，可以进行系统烧录。那么可以进行系统备份了：



### 2、系统镜像修改

在得到img和raw镜像后，一般在raw镜像中进行修改，然后进行烧录，即可实现另一台电脑使用root权限修改板子中的文件内容。

以下为挂载方式：

```
losetup -f
sudo losetup /dev/loop19 system.img.raw
sudo kpartx -a /dev/loop19
sudo mount /dev/loop19 /mnt
```

以下为解挂方式：

```
sudo umount /dev/loop19 /mnt/
sudo kpartx -d /dev/loop19
sudo losetup -d /dev/loop19
```

### 3、系统烧制

将raw镜像拷贝到bootloader文件夹中并改名，即可得到system.img文件，运行刷机指令即可将备份包一起烧入板子中。

