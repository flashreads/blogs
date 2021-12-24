---
id: 001-install-pytorch-windows.md
title: Install Pytorch on Windows
tags:
  - python
  - windows
  - pip
  - pytorch
  - conda
author: Zoran Pandovski
meta-description: How to easily install Pytorch on Windows with one command
date: 2020-05-14 23:30:05 +0200
keywords: python, windows, pip, pytorch, conda
template: post
categories:
  - python
image: assets/images/python/torch.svg
---

## Install Pytorch with pip

The Windows version of PyTorch was never uploaded to PyPi because of the binary size limits. 
When installing it you will end up getting the `RuntimeError: PyTorch does not currently provide packages for PyPI` error.
To successfully install with pip you need to specify the URL locations to the PyTorch wheel: 

```
pip install torch===1.5.0 torchvision===0.6.0 -f https://download.pytorch.org/whl/torch_stable.html

```
>Note that this will install the PyTorch with [CUDA](https://en.wikipedia.org/wiki/CUDA). If your system hasn't an NVIDIA GPU  install the CPU version instead:

```
pip install torch==1.5.0+cpu torchvision==0.6.0+cpu -f https://download.pytorch.org/whl/torch_stable.html
```

## Install Pytorch with Conda

The [Conda](https://docs.conda.io/en/latest/) installation is straight forward:

```
conda install pytorch torchvision cudatoolkit=10.2 -c pytorch
```

and without CUDA:

```
conda install pytorch torchvision cpuonly -c pytorch
```

For additional installation options as LibTorch or installation from Source check the `Start Locally` guide at https://pytorch.org/.
