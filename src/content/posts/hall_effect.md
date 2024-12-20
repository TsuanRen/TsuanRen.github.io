---
title: Hall effect
published: 2024-11-27
description: ''
image: ''
tags: [Hall,Theory]
category: 'Theory'
draft: false 
lang: ''
---

## 磁场下的Ohm's law

在线性响应区间内，Ohm定律适用：
$$
j_\alpha = \sigma_{\alpha\beta}E_\beta \text{\quad and\quad}E_\alpha = \rho_{\alpha\beta}j_\beta
$$
在磁场存在的情况下，上式仍然成立，但 Onsager's reciprocity principle 将被 Time reversal 取代：
$$
\sigma_{\alpha\beta}(\bold B)=\sigma_{\beta\alpha}(-\bold B) \tag{1}
$$
将电导率张量展开为对称张量与反对称张量：
$$
S_{\alpha\beta}=\frac{1}{2}(\sigma_{\alpha\beta}+\sigma_{\beta\alpha})\\
A_{\alpha\beta} = \frac{1}{2}(\sigma_{\alpha\beta}-\sigma_{\beta\alpha})
$$
将$(1)$中的Time reversal 代入上式，不难发现$S,A$分别是$\bold B$的偶、奇函数。假设可以将其展开为$\bold B$的幂级数，则：
$$
S_{\alpha\beta}=(\sigma_0)_{\alpha\beta}+\zeta_{\alpha\beta\gamma\delta}B_{\gamma}B_\delta\\
A_{\alpha\beta} = \epsilon_{\alpha\beta\gamma}A_\gamma=  \epsilon_{\alpha\beta\gamma}\xi_{\gamma\delta}B_\delta
$$
其中，上式利用了反对称张量可以利用$\epsilon_{ijk}$来表示的条件。幂次展开保留到了平方项。Ohm's law 可以重写为：
$$
j_\alpha=S_{\alpha\beta}E_\beta+\epsilon_{\alpha\beta\gamma}E_\beta A_\gamma=S_{\alpha\beta}E_\beta+(\bold E\times \bold A)_\alpha
$$
通常，磁场的平方项贡献很小，可以忽略：
$$
\bold j=\sigma_0\bold E+\bold E\times\bold A,\quad\bold A = \xi\bold B
$$
其中，$\bold E\times\bold A$一项提供了垂直于电场的电流分量，这便是Hall电流，这一项正比于电场与磁场。当磁场为0时，上式回归零场Ohm's law的形式。

综上可见，在Onsager's reciprocity principle存在时，$\sigma$将是对称张量。唯有引入磁场，打破这一关系后，才出现了Hall项。 

## Lorenz对称性及其后果

现有磁场为$\bold B=B\hat z$，自由电子气按照速度$\bold v$相对于实验坐标运动。在满足真空的Lorenz对称性的情况下，可以由Lorenz transformation 得到电子坐标下的场：
$$
\bold E^{(e)} = \bold v\times\bold B, \;\bold B^{(e)}=B\hat z
$$
为了保证电子气的运动不受这一电场偏转，必须存在另一电场，与这一电场平衡：
$$
\bold E=-\bold v\times\bold B=\frac{1}{ne}\bold j\times\bold B
$$
其中，$\bold j = -ne\bold v$为电流密度，$n$为（实空间的）电子密度分布。

:::note 

这一电场可以是预先施加的，$\bold E,\bold B$共同组成了一个“速度选择器”，筛选出了符合的电流$\bold j$。从这一点来看，$\bold E$**维持**了在$\bold B$的偏转作用的阻碍下的稳恒电流$\bold j$，但其并不能形成这一电流，即，这一电流并不受$\bold E$**做功**。而通常情况下，我们考虑的都是存在缺陷对电流造成散射的情况，此时由于存在耗散，故**维持**这一电流必然意味着需要对这一电流**做功**。

:::

不妨从形式上化简上式：
$$
\begin{align}
E_\alpha &= \frac{1}{ne}\epsilon_{\alpha\beta\gamma}j_\beta B_\gamma=\frac{B}{ne}\epsilon_{\alpha\beta z}j_\beta\\
\end{align}
$$
其中：
$$
(\epsilon_{\alpha\beta z})=\left(\begin{matrix} 
0&1&0\\  
-1&0&0\\
0&0&0
\end{matrix}\right)
$$
故：
$$
\bold E = \frac{B}{ne}\left(\begin{matrix} 
0&1&0\\  
-1&0&0\\
0&0&0
\end{matrix}\right)\left(\begin{matrix}j_x\\j_y\\j_z\end{matrix}\right)=\frac{B}{ne}\left(\begin{matrix}j_y\\-j_x\\0\end{matrix}\right)
$$
或者写做Ohm's law的形式：
$$
\bold E = \bold \rho \bold j,\;\rho=\frac{B}{ne}\left(\begin{matrix} 
0&1&0\\  
-1&0&0\\
0&0&0
\end{matrix}\right)
$$

## 弛豫时间近似

在存在磁场的情况下，弛豫时间近似的运动方程（EOM）为：
$$
\frac{\text{d}{\bold {p}}}{\text{d} t} =-e\bold E-e\frac{\bold p}{m}\times \bold B-\frac{\bold p}{\tau}
$$

其中，$\tau$为弛豫时间。粒子间的互作用（散射）越强，$\tau$越小（准粒子寿命越短）。散射项（$-\bold p /\tau$）总是与动量方向相反，为电子的运动提供了阻力。当稳恒电流建立之后，电子动量不再随时间变化，即：
$$
e\bold E+\frac{eB}{m}\bold p\times\hat z+\frac{1}{\tau}\bold p=0
$$
其中，$\bold p=-m\bold j/ne$，回旋频率$\omega_c$（磁场力为向心力的角速度，或圆频率，角速度是一秒转的角度，频率是一秒转的圈数，应该是角速度除去2$\pi$）为$eB/m$。代入上式，得：
$$
e\bold E-\frac{m\omega_c}{ne} \bold j\times\hat z-\frac{m}{ne\tau}\bold j=0
$$
即：
$$
\begin{align}
E_\alpha&=\frac{m}{ne^2}({\omega_c}\epsilon_{\alpha\beta z}+\frac{1}{\tau}\delta_{\alpha\beta})j_\beta
\end{align}
$$
写成矩阵表达式为：
$$
\bold E = \rho\bold j,\;\rho=
\frac{m}{ne^2}\left(\begin{matrix}
\tau^{-1}&\omega_c&0\\
-\omega_c&\tau^{-1}&0\\
0&0&\tau^{-1}

\end{matrix}\right)
$$

这里，Hall项是非对角项（$\rho_{xy},\rho_{yx}$），提供了垂直于电场、磁场的电流，且这一电流正比于电场和磁场。对角项则是常规的电阻率，提供了与电场平行的电流（$\rho_{xx},\rho_{yy},\rho_{zzz}$）。当散射变弱，弛豫时间足够长时，上式便回归了Lorenz对称的情况。

:::tip

实际上，稳恒电流的条件为$(\partial\bold p/\partial t)_r=0$。由于这里动量对于位置矢量$\bold r$仍然是各向同性的，因而可以认为稳恒电流建立时$\text{d}{\bold p}/\text{d}{t}=0$。另外，这里求得的电场是指**稳恒电流建立后**，作用在电流的单电子上的电场。而不是最初的外加电场。这其实并不奇怪，在直流电路中，所谓的电压也是稳恒电流形成之后，末态的电场形成的电压。

:::

## 载流子迁移率





