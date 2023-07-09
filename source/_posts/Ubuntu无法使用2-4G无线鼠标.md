---
title: Ubuntu无法使用2.4G无线鼠标
tags:
  - ubuntu
  - wireless mouse
categories:
  - Ubuntu
abbrlink: c30d67ca
date: 2022-07-18 18:27:16
---

由于最近电脑蓝牙不太稳定，想使用2.4G无线鼠标，但是没有反应。

<!-- more -->

这边记录下解决过程：

1. 移除USB

2. 终端运行命令

```shell
sudo modprobe -r usbhid
```

3. 重新插入USB

反正就解决了 大概就是把可载入模块删了重装吧

中文资料没有找到，具体解决方案可以看[这里](https://askubuntu.com/questions/172533/why-my-wireless-mouse-doesnt-work-in-ubuntu)