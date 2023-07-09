---
title: Ubuntu默认图片查看器打开jpg图片出错
date: 2022-02-02 22:01:38
tags:
    - ubuntu
categories:
    - Ubuntu
---

图片文件无法打开问题

<!-- more -->

![打开时出错](OpenImageError.png)

如图，打开图片文件时提示**分析JPEG图像文件时出错(Not a JPEG file: starts with 0x89 0x50)**

0x89 0x50开头的文件可能为png格式

只需将后缀名改为.png即可使用默认图片查看器打开