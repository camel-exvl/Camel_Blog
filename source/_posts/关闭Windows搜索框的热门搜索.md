---
title: 关闭Windows搜索框的热门搜索
tags:
  - windows
categories:
  - Windows
abbrlink: 9fd7eb26
date: 2023-02-21 15:15:43
---

不知道什么时候开始win10搜索框右下角出现了一个热门搜索的广告。

<!-- more -->

只需执行以下命令添加注册表项目，重启即可关闭。

```powershell
reg add HKCU\Software\Policies\Microsoft\Windows\explorer /v DisableSearchBoxSuggestions /t reg_dword /d 1 /f
```

[参考博客](https://www.winhelponline.com/blog/disable-explorer-search-box-suggestions-windows-7/)
