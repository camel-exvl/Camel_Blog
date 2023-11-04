---
title: Ubuntu下无法使用EasyConnect
tags:
  - easyconnect
  - ubuntu
categories:
  - Ubuntu
abbrlink: 902eae3
date: 2022-02-02 21:59:40
---

EasyConnect问题

<!-- more -->

```shell
zhang-yue@zhang-yue:~$ /usr/share/sangfor/EasyConnect/EasyConnect 
Gtk-Message: 12:47:13.670: Failed to load module "canberra-gtk-module"

(EasyConnect:26442): Pango-ERROR **: 12:47:13.802: Harfbuzz version too old (1.3.1)

追踪与中断点陷阱 (核心已转储)
```

## 解决主要矛盾

错误提示信息是Harfbuzz版本过旧，但[这篇博客](https://www.cnblogs.com/cocode/p/12890684.html)说其实是pango版本过新

所以需要降级pango 但又不能影响系统库 只需将相关依赖直接放在EasyConnect目录下

```shell
zhang-yue@zhang-yue:/usr/share/sangfor/EasyConnect$ ldd EasyConnect | grep pango
	libpangocairo-1.0.so.0 => /lib/x86_64-linux-gnu/libpangocairo-1.0.so.0 (0x00007f7fa0cee000)
	libpango-1.0.so.0 => /lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007f7fa0b54000)
	libpangoft2-1.0.so.0 => /lib/x86_64-linux-gnu/libpangoft2-1.0.so.0 (0x00007f7f9eea9000)
```

不难发现，涉及到的so文件只有这么几个

只需到[这里](https://packages.ubuntu.com/)下载相关`低版本`依赖(按照[这里](https://programmerah.com/error-report-when-running-under-easyconnect-linux-ubuntu-20-04-46024/)的说法应该是低于1.42的版本即可)

> [libpango-1.0-0_1.40.14-1ubuntu0.1_amd64.deb](https://packages.ubuntu.com/bionic-updates/libpango-1.0-0)

> [libpangocairo-1.0-0_1.40.14-1ubuntu0.1_amd64.deb](https://packages.ubuntu.com/bionic-updates/libpangocairo-1.0-0)

> [libpangoft2-1.0-0_1.40.14-1ubuntu0.1_amd64.deb](https://packages.ubuntu.com/bionic-updates/libpangoft2-1.0-0)

解压后将\*\*\*.so和\*\*\*.so.\*\*\*两个文件移入/usr/share/sangfor/EasyConnect/即可(这俩文件在解压后的data/usr/lib/x86_64-linux-gnu中)

(听说似乎.so文件相当于windows的.dll文件)

## 还有一个小问题

至此easyconnect总算是跑起来了 至少能看到图形界面了(心累)

然后就是来解决```Failed to load module "canberra-gtk-module"```的问题了

参考[这里](https://blog.csdn.net/h106140873/article/details/114263954)的方法

```shell
sudo apt install libcanberra-gtk-module
```

芜湖 终于完事了(就是不知为何这玩意打开的速度有点慢)