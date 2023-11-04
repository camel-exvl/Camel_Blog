---
title: Ubuntu设置充电上限
tags:
  - ubuntu
  - battery
categories:
  - Ubuntu
abbrlink: 400346f0
date: 2022-07-18 16:25:37
---

在Windows下，天选2可以直接在华硕服务中设置充电上限，所以在ubuntu下也有了这个需求。

<!-- more -->

在经历过一些失败后(包括但不限于使用TLP)，终于找到了限制充电上限的方法。

使用[bat](https://github.com/tshakalekholoane/bat)就行啦

# 安装
下载bat(二进制文件)后，进行安装

```shell
sudo install bat /usr/local/bin
```

# 查看阈值

```shell
bat -t
# bat --threshold
```

# 设置阈值

```shell
sudo bat -t <CHARGE_THRESHOULD>
# sudo bat --threshold <CHARGE_THRESHOULD>
```

# 永久修改

默认状态下，设置后的阈值会在重启后失效，恢复默认状态。

使用以下指令可以永久修改阈值：

```shell
sudo bat -p
# sudo bat --persist
```

# 重置阈值

```shell
sudo bat -r
# bat --reset
```

# 查看当前电量

```shell
bat -c
# bat --capacity
```

# 查看充电状态

```shell
bat -s
# bat --status
```

不过其实我在使用这个命令后显示的是```unknown```，不知道为什么。

但是可以通过观察笔记本上的充电指示灯来判断状态，这也无伤大雅。


总的来说非常简单，具体原文可以看[这里](https://www.linuxuprising.com/2021/06/easily-set-charging-thresholds-for-asus.html)