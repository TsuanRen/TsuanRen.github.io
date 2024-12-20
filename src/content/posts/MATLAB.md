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

1. 在使用matlabのapp的时候，经常会因为路径问题，需要来回切换工作文件夹。其实app在启动的时候，startupfcn是可以被执行的。只需要利用这一点，在startup时加入addpath(pwd)即可。(pwd可以获取函数所在路径，addpath类似于import，为临时添加路径)。
1. 值得注意的是，在startupfcn中运行的pwd和其他函数中的pwd结果并不一致。似乎在启动app的时候matlab会切换当前文件夹。
1. 制表符在disp中不能用'\t'表示，可以使用char(9)来代替。而在fprintf中则可以使用。
