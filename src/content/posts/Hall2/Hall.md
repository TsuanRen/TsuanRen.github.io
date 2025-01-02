---
title: Hall Effect: Integer
published: 2024-12-31
description: ''
image: ''
tags: []
category: ''
draft: false 
lang: ''
---



## AB相位

将Berry Phase中的状态空间修改为矢势空间，可以得到AB相位的形式。二者均为几何相位。当电子绝热地绕如图螺线管外侧一圈后，会相比初态获得一个相位：

![](./Hall2/1.svg)

其中，相位因子正比于磁通量：
$$
\theta = \frac{q\Phi}{\hbar}
$$


## Corbino Disc

![](./Hall2/2.jpg)

现有一个圆环系统。圆环域用于模拟周期性晶格。中心空白处施加变化磁通，由Maxwell equations：
$$
\vec E=-\partial_t\vec A-\nabla\phi
$$
令$x$轴沿着切向($\hat \theta$)，$y$轴沿着径向($\hat r$)。我们想模仿Hall effect的构型，利用这个含时磁通来构建一个沿着$x$轴方向的电场，需要一个沿着$x$方向的矢势：
$$
\vec A=-Et\hat\theta
$$
取其旋量，得磁感应强度：
$$
\begin{align}
\nabla\times \vec A&=\frac{1}{r}\hat z(\partial_r(rA_\theta)-\partial_\theta A_r)\\
&=\frac{1}{r}\hat z(-Et)
\end{align}
$$
由此可得磁通为：
$$
\Phi = \iint \frac{1}{r}(-Et)r\dd\theta\dd r=-(2\pi r_0E)t
$$


