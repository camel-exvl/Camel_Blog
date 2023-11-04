---
title: Windows下使用neofetch
tags:
  - windows
  - neofetch
categories:
  - Windows
abbrlink: d1aa9b96
date: 2022-07-30 16:46:02
---

闲得无聊在Windows下也整个neofetch

<!-- more -->

# neofetch

获取scoop(一个包管理器)

```powershell
iwr -useb get.scoop.sh | iex
```

获取neofetch

```powershell
scoop install neofetch
```

# ScreenFetch

还有一个功能类似的玩意：ScreenFetch

在PowerShell 5中，直接安装ScreenFetch即可使用

```powershell
Install-Module -Name windows-screenfetch
```

然而这样的安装在PowerShell 7中会有问题 无法正常使用

一个可行的解决方法：

在```Windows PowerShell 5```中安装```windows-screenfetch```

将```C:\Program Files\WindowsPowerShell\Modules\windows-screenfetch```复制到```C:\Users\<username>\Documents\PowerShell\Modules```下

从[Github仓库](https://github.com/JulianChow94/Windows-screenFetch)中获取最新的[Data.psm1文件](Data.psm1)，替换原有的```Data.psm1```，重启PowerShell后即可使用ScreenFetch



此方法来自[博客](https://blog.csdn.net/yihuajack/article/details/106234124)