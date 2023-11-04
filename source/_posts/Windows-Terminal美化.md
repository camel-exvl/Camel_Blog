---
title: Windows Terminal美化
tags:
  - windows
  - terminal
categories:
  - Windows
abbrlink: f7a47aab
date: 2022-07-30 17:08:14
---

适当的美化可以使Windows Terminal变得同样赏心悦目。

<!-- more -->

# Windows Terminal

微软于19年发布的这个[Windows Terminal](https://www.microsoft.com/zh-cn/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab)集成了PowerShell、CMD、WSL等，而且比较美观。

当然，默认设置下的Windows Terminal比较朴素，需要亿点点的美化。

> 以下内容均在PowerShell 7下运行

# oh-my-posh

[oh-my-posh](https://ohmyposh.dev/)是一款主题管理工具，可直接在[微软商店](https://apps.microsoft.com/store/detail/XP8K0HKJFRXGCK)中进行安装。

安装完成后，使用命令

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

进行初始化

## 字体安装

oh my posh 使用的图标来自于[Nerd Fonts](https://www.nerdfonts.com/)字体，因此为了更好的显示效果，需要安装相关的字体。其中官方建议安装[Meslo LGM NF](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Meslo.zip)字体。

字体安装完成后，需要对配置终端使用字体。在终端按下默认快捷键```Ctrl+Shift+,```打开```settings.json```文件，在"profiles"中添加如下内容：

```json
{
    "profiles":
    {
        "defaults":
        {
            "font":
            {
                "face": "MesloLGM NF"
            }
        }
    }
}
```

## 主题选择

美化终端界面，当然需要选择喜欢的主题。

使用命令

```powershell
Get-PoshThemes
```

获取所有支持的主题。

选定主题后，打开配置文件(这个文件里的内容会在每次打开终端时自动运行)


```powershell
code $PROFILE
```

当然这里使用notebad之类的也可以

在文件中加上这么一句：

```powershell
oh-my-posh init pwsh --config ~/.peru.omp.json | Invoke-Expression
```

其中peru为选择的主题

配置完成后使用

```powershell
. $PROFILE
```

重新加载配置

## 遇到的问题

### 选择主题后没有变化

只需要把配置的那句话改为

```powershell
oh-my-posh init pwsh --config "C:\Program Files (x86)\oh-my-posh\themes\peru.omp.json" | Invoke-Expression
```

使用绝对路径就可以了

### 终端内无法使用代理下载

在配置文件($PROFILE)中加上

```powershell
$Env:http_proxy="http://127.0.0.1:7890";
$Env:https_proxy="http://127.0.0.1:7890";
```

即可。(其中7890为clash端口号)