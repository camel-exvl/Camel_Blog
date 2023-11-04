---
title: Ubuntu美化
tags:
  - ubuntu
  - gnome
categories:
  - Ubuntu
abbrlink: 4d7d1fbc
date: 2022-01-14 23:22:09
---

默认的主题有点丑 需要亿点点美化

<!-- more -->

# gnome

安装相关工具

```shell
sudo apt install gnome-tweak-tool
sudo apt install gnome-shell-extensions
sudo apt install chrome-gnome-shell
```

[gnome官方插件中心](https://extensions.gnome.org/)

打开

```shell
gnome-tweaks
```

> 重启gnome只需alt+F2 输入r即可

# 插件

- dash to dock

> 更改dock栏 需隐藏原有dock栏

```shell
cd /usr/share/gnome-shell/extensions
sudo mv ubuntu-dock@ubuntu.com ../
```

# 主题

GTK Theme: 构建应用程序的图形用户界面的框架

Gnome Shell Theme: Shell元素主题

[gnome主题下载](https://www.gnome-look.org/s/Gnome/browse/)

[Canta theme](https://www.gnome-look.org/s/Gnome/p/1220749)