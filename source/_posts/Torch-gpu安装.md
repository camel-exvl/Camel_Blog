---
title: Torch-gpu安装
tags:
  - python
  - torch-gpu
categories:
  - 技术记录
abbrlink: 506bf8d8
date: 2022-08-24 11:09:26
---

python默认安装的torch是cpu版的，无法使用gpu进行训练。这边简单记录一下torch-gpu安装方法。

<!-- more -->

nvidia-smi查看cuda版本

在[官网](https://pytorch.org/get-started/locally/#no-cuda-1)生成安装链接进行安装

注意安装前先把原来的torch删了 然后安装的时候不要用清华镜像。

后面加-i https://pypi.org/simple

---

代码里用print(torch.__version__)查看torch版本

显示1.10.2+cpu 即为cpu版本 显示1.11.0+cu113即为gpu版本

```python
print(torch.cuda.device_count()) 
print(torch.cuda.is_available())
```

查看可用gpu数量和可用状态

---

安装CUDA Toolkit https://developer.nvidia.com/cuda-toolkit-archive 

安装CUDNN https://developer.nvidia.com/[rdp](https://so.csdn.net/so/search?q=rdp&spm=1001.2101.3001.7020)/cudnn-download

[教程视频](https://www.bilibili.com/video/BV1Rz411e7eJ?spm_id_from=333.999.0.0&vd_source=f6a9c6152995529b9a7e52ad6f79a2d6)

---

可用以后代码中有的没的地方加点.cuda() .cpu() 进行CPU GPU数据交换即可使用GPU来训练人工智能

http://www.codebaoku.com/it-python/it-python-248324.html