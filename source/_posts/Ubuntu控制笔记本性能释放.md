---
title: Ubuntu控制笔记本性能释放
tags:
  - ubuntu
categories:
  - Ubuntu
abbrlink: ee10d497
date: 2022-06-18 20:18:08
---

在使用Ubuntu时发现性能无法得到完全释放，风扇转速也十分有限。

<!-- more -->

型号：华硕 天选2

# 一、问题描述

在Win10中，电脑可使用Fn+F5切换性能释放模式（静音、平衡、增强），因此有了在Ubuntu下调整模式的想法。

# 二、一些尝试

参照网络某些博客使用lm-sensors后，发现找不到可调节的风扇，并没有达到预期效果。

# 三、解决方式

这种方式应该仅限于华硕笔记本。

> In Kernel 5.6 there is a fan mode for asus laptops, check if you have /sys/devices/platform/asus-nb-wmi/throttle_thermal_policy 2 - Silent, 0 - Balance, 1 - Turbo, similar to the modes in armoury crate on windows.

在/sys/devices/platform/asus-nb-wmi/throttle_thermal_policy内存储的数字即为当前模式：

其中默认的0代表平衡模式，1代表增强模式，2代表静音模式。

所以解决方法就很简单啦 修改该文件的值即可。

在这边也简单记录下命令。

```bash
su  # 需要权限
echo 1 > /sys/devices/platform/asus-nb-wmi/throttle_thermal_policy # 切换为增强模式
echo 0 > /sys/devices/platform/asus-nb-wmi/throttle_thermal_policy # 切换为平衡模式
echo 2 > /sys/devices/platform/asus-nb-wmi/throttle_thermal_policy # 切换为静音模式
```

嫌命令麻烦的话也可以看看这个[仓库](https://github.com/leonmaxx/asus_fanmode)，不过我没试过。

# 四、参考资料
[How to control fans on an asus laptop](https://askubuntu.com/questions/1254364/how-to-control-fans-on-an-asus-laptop?newreg=90b0e4d9f8ce481fa9370b5544606c8d)


