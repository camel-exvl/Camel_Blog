---
title: Ubuntu无法识别无线网卡
date: 2022-02-05 12:31:00
tags:
    - ubuntu
categories:
    - Ubuntu
---

安装Ubuntu后惊奇地发现莫的Wi-Fi

<!-- more -->

品牌: 天选2 (ASUS TUF Gaming A15 FA506QM_FA506QM)

网卡: MediaTek MT7921

OS: Ubuntu 20.04.3 LTS x86_64

# 问题: 
Ubuntu安装完成后，设置中无Wi-Fi选项卡，找不到无线网卡(好像没有驱动程序)

似乎只用在较新(2021.6)的电脑型号中会出现这类问题

# 解决：

(这问题着实困扰了我很久，一直都没法正常使用Ubuntu 连不上Wi-Fi也用不了蓝牙

为适配最新硬件，需要将Linux内核升级到最新

刚完成安装的Ubuntu 20.04.3 使用的是5.11内核，无法正常支持MT7921网卡

因此需要自行更新内核版本(可能有一定风险)


> 可以暂时选择使用有线网络或者共享网络完成后续安装工作
> 我使用的是手机USB共享网络

## 查询内核版本

```shell
uname -r
5.11.0-36-generic
```

## 下载安装ubuntu-mainline-kernel.sh脚本

```shell
wget https://raw.githubusercontent.com/pimlie/ubuntu-mainline-kernel.sh/master/ubuntu-mainline-kernel.sh
sudo install ubuntu-mainline-kernel.sh /usr/local/bin/
```

查看最新内核版本

```shell
ubuntu-mainline-kernel.sh -c
```

查看所有可用内核版本

```shell
sudo ubuntu-mainline-kernel.sh -r
```

## 安装新内核

```shell
sudo ubuntu-mainline-kernel.sh -i
//或指定安装版本
sudo ubuntu-mainline-kernel.sh -i 5.12.11
```

(亲测5.12.11版本内核仍无法解决问题 需要更新的内核版本)

在默认情况下 重启时系统会默认使用最新的内核

但也可以在启动系统时选择进入高级模式，指定所需要的内核

## 安装固件文件

```shell
sudo apt install linux-firmware
```

问题解决

不过注意关机后不要立即开机 等待半分钟到一分钟左右

不然两个系统都无法识别无线网卡(不知道为啥 但影响不大就不管它了)

# 参考资料

https://miloserdov.org/?p=6899
