---
title: MATLAB简单技巧
published: 2024-12-12
description: 'Coding'
image: ''
tags: [Coding,Matlab]
category: 'Coding'
draft: false 
lang: ''
---

1. 在使用matlabapp的时候，经常会因为路径问题，需要来回切换工作文件夹。其实app在启动的时候，startupfcn是可以被执行的。只需要利用这一点，在startup时加入addpath(pwd)即可。(pwd可以获取函数所在路径，addpath类似于import，为临时添加路径)。
