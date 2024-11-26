---
title: More about shirley
published: 2024-11-26
description: ''
image: './More_about_shirley/1.jpg'
tags: [XAS, XPS, ARPES, Data processing]
category: 'ARPES'
draft: false 
lang: ''   
---

XAS是一种常见的用于表征物质电子结构的方法，其常见的一种测量方法是，利用X射线照射样品，产生光电子，样品荷电，产生电流转导至地。产生光电子越多，样品荷电越多，产生电流越大。而在实际测量的XAS中，常见低能端峰位更高的现象，这便是本底信号所致。本底产生于深度激发的电子在样品中的能量损耗。为了扣除本底，出现了种种数学模型，如此处的Shirley。

Shirley本底扣除方法中，其基本假设是：高能端的电子将部分地被非弹散射，形成低能端电子的本底噪声。定量地说便是，对于初态能量为E的光电子，在到达探测器之前：

1. 受到非弹散射而跃迁至任意能量为$\epsilon<E$的末态的概率（密度）是不依赖于始末态的常数：

$$
\forall\epsilon<E,p(E\rightarrow\epsilon)=p_0
$$

2. 损失能量的电子数$\text{d}{n'}$正比于总的电子数（$\text{d}{n}+\text{d}{n'}$），其比例系数是一个不依赖于始末态的常数：

$$
\text{d}{n'}(E)=\alpha(\text{d}{n}(E)+\text{d}{n'}(E))
$$

记测量的光谱曲线为$J(E)$，本底为$S(E)$，原谱减去本底得到的校正谱为$J(E)-S(E)$。校正谱为弹性散射的电子信号，处于$[E,E+\text{d}{E}]$区间内的电子数$\text{d}{n}$正比于该区间的信号强度（假设比例系数在很窄的能量区间内不依赖于能量，实际上，光电子强度与入射光强度、跃迁概率等均有关）：
$$
\text{d}{n}(E)=\beta[J(E)-S(E)]\text{d}{E}
$$
代入基本假设2，可以解出$\text{d}{n'}$：
$$
\text{d}{n'}=\frac{\alpha\beta}{1-\alpha}[J(E)-S(E)]\text{d}{E}
$$
这些电子将按照$p_0\text{d}{\epsilon}$为概率，为$[\epsilon,\epsilon+\text{d}{\epsilon}]$区间内提供本底信号强度：
$$
S(\epsilon,E)\text{d}{\epsilon}=\frac{\alpha\beta p_0\text{d}{\epsilon}}{1-\alpha}[J(E)-S(E)]\text{d}{E}
$$
其中，$S(\epsilon,E)\text{d}{\epsilon}$表示初态为能量$E$的电子在能量$\epsilon$处形成的那一部分本底信号强度。因而，总的本底信号是对所有$E>\epsilon$的求和：
$$
S(\epsilon)=\sum_{E=\epsilon}^{+\infty}S(\epsilon,E)
=S\left( \varepsilon \right) =k\int_{\varepsilon}^{+\infty}{\left[ J\left( E \right) -S\left( E \right) \right] \text{d}E}
$$
其中，$k=\frac{\alpha\beta p_0}{1-\alpha}$。注意到若能量为$\epsilon$处并没有峰，则该处的信号均为本底，$J(E)-S(E)=0$，因而：

1. 若$\epsilon$处有峰。假设$E_b$为峰的高能边（边界），则：

$$
S\left( \varepsilon \right) =k\left\{ \int_{\varepsilon}^{E_b}{\left[ J\left( E \right) -S\left( E \right) \right] \text{d}E}+\sum_{E_j>\varepsilon}{\int_{E_j}^{E_j+\Delta E_j}{\left[ J\left( E \right) -S\left( E \right) \right] \text{d}E}} \right\}
$$

其中，$E_j$为其他峰的低能边。上式不难化简为：
$$
S(\epsilon) =kQ(\epsilon)+b'
$$
式中，$Q(\epsilon)=\int_\epsilon^{E_b}[J-S]\text{d}{E}$为校正谱处于$\epsilon$与$E_b$之间的面积，而$b'$则取决于该峰与其他峰的相对位置。在该峰区域内，$b'$是不依赖于$\epsilon$的常数。

2. 若$\epsilon$处无峰。则：

$$
S\left( \varepsilon \right) =k\sum_{E_j>\varepsilon}{\int_{E_j}^{E_j+\Delta E_j}{\left[ J\left( E \right) -S\left( E \right) \right] \text{d}E}}
$$

这是一个不依赖于$\epsilon$的常数（只要$\epsilon$在变化时不跨越任何有峰的区域）。这表明，按照Shirley的假设，两个峰位之间应该均是水平的区域，这些水平的区域会随着能量的降低，像台阶一样逐步升高（每跨越一个峰，均是上一个台阶）。

至此，我们描绘了Shirley假设下，光电子谱应该有的峰形。在使用Shirley时，我们或许需要尽量保证原谱符合其描述的情况：即峰位左右侧为水平、且高能边低于低能边。否则，贸然采用Shirley或许并不合理。

下面是求解Shirley的算法部分。首先假设某峰的高能边（$E_b$）和低能边（$E_a$）的高度$J(E_a)=S(E_a)=a,J(E_b)=S(E_b) = b$。结合$S(\epsilon)=kQ(\epsilon)+b'$，可得：
$$
b'=b, k=\frac{a-b}{I},I=\int_{E_a}^{E_b}[J(\epsilon)-S(\epsilon)]\text{d}{\epsilon}
$$
其中$I$便是校正谱中，该峰的总面积。不妨定义泛函：
$$
\psi[S(\epsilon),E]=\int_{E}^{E_b}[J(\epsilon)-S(\epsilon)]\text{d}{\epsilon}
$$
则有：
$$
S(\epsilon)=b+(a-b)\frac{\psi[S(\epsilon),E]}{\psi[S(\epsilon),E_a]}
$$
上式的右侧可以视为$S(\epsilon)$的泛函，它将$S(\epsilon)$映射为另一函数。而这一映射的结果得到了$S(\epsilon)$自身，这表明，上式的解便是这一泛函的不动点。在某些情况下，我们可以通过不断迭代函数来得到函数的不动点，如：
$$
a_1=f(x),a_2=f(f(x)),\cdots,f(a_{\infty})=a_\infty
$$
算法求解Shirley时，便是采用这一迭代法。
