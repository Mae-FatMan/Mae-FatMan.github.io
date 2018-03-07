---
layout: post
title:  "安装Ubuntu-12.04.4 desktop和server版本"
date:   2018-03-07 14:32:21
categories: Markdown
---
### 导语
新项目启动需要安装Linux系统，通过各个版本之间的对比，综合考虑稳定性等，最后选中了ubuntu-12.04.4这个版本，本地使用ubuntu-12.04.4-desktop-amd64.iso，服务器端使用ubuntu-12.04.4-server-amd64.iso。

下载地址：http://old-releases.ubuntu.com/releases/12.04.4/

### 步骤
#### 一，制作U盘启动器
先在windows上安装Ultraiso软件，打开后选择要安装的iso镜像，启动——写入硬盘镜像，选择USB-HDD+方式，格式化U盘，接着点击写入，带写入完成退出U盘。

#### 二，PC Bios启动U盘安装系统
本地端安装desktop版本，Bios启动选用U盘，傻瓜式，无需多做其他。

服务器端安装server版本，要注意一下几点：
* 通过U盘启动后点击Ubuntu server install；
* 进入选择语言等界面，是否扫描和配置键盘选择否-No，开启自动安装报错；
* 提示错误从光盘中读取数据出错（cdrom程序检测出错），有两种办法，一种使用win32diskimager这款软件进行刻录，另外一种
	按ALT+F2切换到另一个Console，输入以下命令： 
	umount /dev/sdc4    //sdc4是我的U盘设备，不同机器可能不一样，可用"ls /dev |grep sd*"查看一下。
	mkdir /mnt/usb      
	mount -t vfat /dev/sdc4 /mnt/usb //将U盘挂载到这个文件夹下
	cd /mnt/usb
	mount -o loop ubuntu-12.04.4-server-amd64.iso /cdrom //挂载iso文件
	ATL+F1,选择YES，重新扫描、继续安装。
* 安装软件open-sshserver（方便远程登录）、Ubuntu home（方便桌面操作）
* 网络配置跳过、选择自动更新安全包

安装过程可参考
https://www.linuxidc.com/Linux/2017-11/148341.htm

 