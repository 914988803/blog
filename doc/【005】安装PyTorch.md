---
title: 安装PyTorch
date: 2022-05-08
tags:
       - PyTorch
       - pip
       - 镜像安装
categories: python
---

我的CUDA版本是11.4

使用pip命令安装，使用镜像站加速）（-i）

```
pip3 install torch torchvision torchaudio -f https://download.pytorch.org/whl/cu114/torch_stable.html -i https://mirrors.ustc.edu.cn/pypi/web/simple/
```

其他镜像站

- 清华大学开源软件镜像站：https://mirror.tuna.tsinghua.edu.cn/help/pytorch/
- 中科大开源镜像站：https://mirrors.ustc.edu.cn/help/pytorch.html
- 阿里云 PyTorch 仓库：http://pytorch-cn-gpu.s3-website.cn-northwest-1.amazonaws.com.cn/


