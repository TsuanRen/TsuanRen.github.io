---
title: kz_mapping
published: 2024-11-25
description: 'My Kz-Mapping Method introduction'
image: ''
tags: []
category: ''
draft: false 
lang: 'Chinese'
---

### 单电子末态近似与$k_z$-Mapping

在自由电子末态近似中，电子的动量分量为：
$$
k_z = 0.512\sqrt{E_{kin}\cos^2\theta_x+V_0}\\
k_{x}=0.512\sqrt{E_{kin}}\sin\theta_{x}\\
k_y=0.512\sqrt{E_{kin}}\cos\theta_{x}\sin\theta_y
$$
其中，$x$方向沿着分析器的Slit方向（Slit平行于样品），$y$方向垂直于Slit并平行于样品表面，而$z$方向则垂直样品表面。$E_{kin}$指费米能级处逸出光电子的动能（$\hbar\omega-\phi$）。注意，$E_b$指的是电子的结合能，而 $E_{kin}$指的是该光子能量下从Fermi level处逸出的光电子动能。若用$E$表示该光电子能量下某一光电子的动能，则该光电子逸出前的结合能便是：$E_b=E-E_{kin}$。

​      实验中，测试$k_z$-mapping时，通常会按1~2 eV为间距，等间距地改变光子能量。每个光子能量下，均保证在$\theta_y=0$的情况下，沿着$\theta_x$（Slit）方向测CUT。对这些CUT汇总，进行几何变换，便得到了$k_z$-mapping。下图是一个二维特性材料的例子：

<img src = "kz_mapping\kzcontour.png" style="zoom:50%;" >

### 确定Mapping的Contour图像区域

由于$k_x-k_y$面内的等能面构成的实际为一段圆弧，即：
$$
k_x^2+k_z^{2}=(0.512)^2E_{kin}+V_0
$$
其中，$\theta_x$的几何意义如下图所示。等能面为圆弧DBC，其半径为$\sqrt{(0.512)^2E_{kin}+V_0}$，FJE是半径为$0.512\sqrt{E_{kin}}$的圆弧。两端的圆弧中心皆为动量零点。过能量为$E_{kin}$的等能面上某点向$x$轴做垂线，交FJE圆弧于J点，则∠AJH便是该能量$E_{kin}$下，点I的$k_x$对应的$\theta_x$。这一角度略大于∠JAB。$V_0$越大，这一差距越大。

<img src ="kz_mapping\geo.jpg" style="zoom:33%;" >

​      当我们沿着$\theta_y=0$的直线方向，等间隔地变光子能量来扫描$\theta_x-E$的Cut时，在$k_x-k_z$中走过的路径如下所示。由于需要一个矩阵来保存这样的扇形数据，故要首先确定需要保存的矩形区域。区域的边界可以通过最低、最高能量的圆弧来确定。图中红色边框上的几个箭头强调了这些关键位置。

<img src = "kz_mapping\bzcut.png" style="zoom: 50%;" >

​      在程序中，首先会确定光子能量序列、文件名序列，还需要事先假定一个$V_0$（后续需要通过调整$V_0$，把图像调整到一个合适的周期，这个周期应该符合XRD测试的z轴周期）。然后计算能量最高、最低的两组数据确定的矩形边界。矩阵的尺寸可以自己定义，尽量保证尺寸在各个维度上大于原先的尺寸。

​      或者也可以用这样一种方法确定：由于低能段的信息密度较高，因而按照低能端的数据尺寸来确定矩阵的尺寸。比如该组数据在$k_x\in[-a/2,a/2]$的区间中有$n$个点，而矩形区域的$k_x$边界为$[-b/2,b/2]$，则最终的矩阵应该有round(n/a*b)列。矩阵的行则通过高能端确定，应该保证在圆弧两侧，每一行只包含一个或两个数据。

### 数据的变换

首先将原先的一系列CUT拼成3D矩阵（MAP），以备线性插值。再新建一个全零3D矩阵（NMAP），用于保存变换后的结果。NMAP的行、列、层坐标分别为$(E_b,k_x,k_z)$，而原矩阵的坐标为$(E_b,\theta,E_{kin})$。从某个能量位置出发，对两个矩阵分别进行二维切片，得到NSlice和Slice。NSlice中的某矩阵元对应的k空间的点$(k_x,k_z)$通过上述公式可以逆映射至$(\theta,E_{kin})$，通过对Slice的线性插值可以得到这一点上的值，将这一值赋给NSlice。将所有这样得到的NSlice重建为3D矩阵，便得到了一个$k_z$-mapping.

<img src = "kz_mapping\transform.png" style="zoom:33%;" >



#文中采用的CUT数据为Seinta公司的DA30L仪器在SES操作界面下，通过Fixed模式得到的txt格式文件。
