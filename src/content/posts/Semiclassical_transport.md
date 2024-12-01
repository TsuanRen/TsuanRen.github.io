---
title: Semi-classical transport
published: 2024-12-01
description: 'Semi-classic electron transport model with the Bolzmann transport equation.'
image: ''
tags: [Fermi liquid, Theory]
category: 'Theory'
draft: false 
lang: ''
---

输运理论：在 Semi-classic Bloch electron 的理论框架下，求解输运物理量时，需要首先求解分布函数。通过假设 1）局域平衡分布；2）稳恒状态并引入碰撞项，可以得到分布函数的动力学方程。在此基础上，引入弛豫时间近似，可以将碰撞项取为利于求解方程的形式。至此便得到了 Bolzmann 输运方程。

----------------

分布函数指粒子出现在某态上的概率。对于半经典的Block电子波包（外场波长>>波包宽度>>晶格常数），分布函数可以理解为在相空间$\{(k,r)\}$上的一点$(k,r)$处的粒子数密度（0~1）。其中，省略了$k,r$的矢量符号，在使用时注意甄别。

电子分布函数可以表示为：
$$
f(k,r;t)\equiv f(k(t),r(t);t)\equiv f(t)
$$
需要注意，函数$f$最终仅仅依赖于时间$t$，因为$k,r$均依赖于时间。又要注意$f\neq f(k(t),r(t))$，也就是说，即便$k,r$不随时间变化，分布函数也允许随时间改变。

---------

半经典电子的运动方程为：
$$
\begin{align}
\frac{\text{d} r}{\text{d} t}&=\frac{1}{\hbar}\partial_k\epsilon(k)\\
\hbar\frac{\text{d} k}{\text{d} t}&=-e[E(r,t)+\frac{\text{d} r}{\text{d} t}\times B(r,t)]
\end{align}
$$

需要注意，此处的能带色散$\epsilon(k)$略去了带指数，这样做**忽略了带间跃迁**的可能性，电子运动的相空间代表某个特定带指数下的Bloch电子状态集合。

-------------

上式的形式需要我们注意“偏微分”与“全微分”两种不同的表达：
$$
\begin{align}
\frac{\partial f}{\partial t}=\frac{f(k,r,t+\text{d} t)-f(k,r,t)}{\text{d} t}\\
\frac{\text{d} f}{\text{d} t}=\frac{f(k+\frac{\text{d} k}{\text{d} t}\text{d} t,r+\frac{\text{d} r}{\text{d} t}\text{d} t,t+\text{d} t)-f(k,r,t)}{\text{d} t}
\end{align}
$$
如果观察$(k,r)$构成的相空间，前者意味着盯住相空间中一个定点，观察该处体积元内的“点子数目”（或称为相空间电子密度，简称相密度。这里，分布函数的值是一个抽象的概率，同样也可以被可视化为“点子”的密度分布）的变化。而后者则是在追踪相空间中的一条运动轨道（因为$k,r$依赖于时间，因而构成轨道，不同的初值会引向不同的轨道），观察该轨道在$t$时刻时对应的点处的相密度。

------

该分布函数建立在局部平衡的假设之上。即，位于$r$处的某物理小体积中的小系统在任意时刻$t$均处于平衡状态，或说其弛豫时间极短，可以立刻达到平衡。该小系统中的电子的波矢量便是$k$。若体系处处处于平衡态（温度均匀、无外场），则该函数退化为Fermi分布函数：
$$
f_0(k,r)=\frac{1}{1+\exp(\frac{\varepsilon(k)-\mu(r)}{k_BT(r)})}
$$
当仅存在外场，不存在散射时，同一体积元内的电子将沿着相同的轨道运动，因而这一轨道上的电子态密度处处相等，因而有：
$$
\frac{\text{d} f}{\text{d} t}=0
$$
而散射的引入使得不同轨道之间出现了电子的交换。

----------

可以人为将分布函数分割为两个部分：**相轨道**与**相密度场**。前者通过参数方程$k=k(t),r=r(t)$表示，由电子的半经典方程描述，因而轨道彼此不允许交叉。后者通过多元函数$\rho=f(k,r,t)$表示，依赖于系统的实际状态。

由于相密度场本质上是由粒子数密度构成的场，其变化需要服从于粒子的运动方程。两个部分需要满足**一致性条件**。如下文所述：

当*不计入散射时，粒子运动严格依赖于动力学方程*，即不允许轨道交叉，$\text{d} f/\text{d} t =0$：
$$
\frac{\partial f}{\partial k}\frac{\text{d} k}{\text{d} t}+\frac{\partial f}{\partial r}\frac{\text{d} r}{\text{d} t}+\frac{\partial f}{\partial t}=0
$$
这里，我们已经选取了$k,r,t$作为$f$的宗量，因而偏微分具有省略的形式，例如：$\partial f/\partial k \equiv (\partial f /\partial k)_{r,t}$

当存在外场时，上式不再成立。引入碰撞项($\xi(k,r,t)$)来衡量散射造成的影响。即$\text{d} f/\text{d} t = \xi $

---------------------------------

所谓的**稳态**，即相密度场不随时间改变：
$$
\frac{\partial f}{\partial t}=0
$$
更形象地说，就是固定在相空间座标架上的点的态密度恒定不变。因而态密度随时间的变化完全由于电子在相空间中沿着轨道的运动。非平衡稳态是由于电子在相空间的移动过程中建立起来的。

--------

对于**存在散射的非平衡稳态**系统中的电子，其一致性条件为：
$$
\frac{\partial f}{\partial k}\frac{\text{d} k}{\text{d} t}+\frac{\partial f}{\partial r}\frac{\text{d} r}{\text{d} t}=\xi(k,r,t)
$$
通过半经典电子运动方程，引入外场的作用。上式的左侧第一项为：
$$
-\frac{e}{\hbar}\frac{\partial f}{\partial k}\cdot(E+\dot{r}\times B)
$$
注意到:
$$
f=f_0+f_1
$$
即，非平衡稳态的分布函数仅仅对平衡分布$f_0$有一个小的偏离$f_1$。在这里，我们将$f_0$作为零级近似，仅当零级近似项为零的情况下，才考虑$f_1$的影响。对于偏微分的情况，我们假设$f_1$在相空间是缓变的，其变化速度小于$f_0$。如，对于磁场项，由于：
$$
\frac{\partial f_0}{\partial k}=\frac{\partial \epsilon}{\partial k}\frac{\partial f_0}{\partial \epsilon}=\hbar\frac{\partial f_0}{\partial \epsilon}\dot{r}
$$
而$\dot{r}\cdot (\dot{r}\times B)=B\times(\dot r\cdot \dot r)=0$，故磁场项的零级项为零，需要考虑$f_1$的影响：
$$
-\frac{e}{\hbar}\frac{\partial f}{\partial k}\cdot(\dot r \times B)=-\frac{e}{\hbar}\frac{\partial f_1}{\partial k}\cdot (\dot r\times B)
$$
而电场项中$f_1$的影响较小：
$$
-\frac{e}{\hbar}\frac{\partial f_0}{\partial k}\cdot E=\frac{\partial f_0}{\partial\epsilon}\dot{r}\cdot (-eE)
$$
已经假设$\partial f_0/\partial k\gg \partial f_1/\partial k$。因而要观察到输运现象中的磁效应，往往需要：
$$
\abs{v_F\times B}\gg \abs{E}
$$

------------------------

对坐标的微分项如下：
$$
\frac{\partial f_0}{\partial r}\cdot \frac{\text{d} r}{\text{d} t}=\left(\frac{\partial f_0}{\partial \mu}\frac{\text{d} \mu}{\text{d} r}+\frac{\partial f_0}{\partial T}\frac{\text{d} T}{\text{d} r}\right)\cdot \frac{\text{d} r}{\text{d} t}
$$
考虑其中的化学势项，
$$
\partial_\mu f_0=\frac{1}{(1+\exp(\cdots))^2}\times\exp(\cdots)\times\frac{1}{k_BT}=\frac{f_0-f_0^2}{k_BT}=\frac{f_0(1-f_0)}{k_BT}\\
\partial_\mu f_0\frac{\text{d} \mu }{\text{d} r}\cdot\dot r=\frac{1}{k_BT}f_0(1-f_0)\dot r\cdot\nabla\mu
$$
其中：
$$
\partial_\epsilon f_0=\frac{-\exp(\cdots)}{(1+\exp(\cdots))^2}\times\frac{1}{k_BT}=\frac{1}{k_BT}(f_0^2-f_0)=-\frac{1}{k_BT}f_0(1-f_0)
$$
注意到电场是电势能的负梯度，因而电场项可以表示为：
$$
\partial_\epsilon f_0=-\partial_\mu f_0\\
\partial_\epsilon f_0\dot r\cdot (-eE)=\frac{1}{k_BT}f_0(1-f_0)\dot r\cdot \nabla U
$$
可见化学势项和电场项可以合并为**电化学势**项：
$$
\frac{1}{k_BT}f_0(1-f_0)\dot r\cdot \nabla(\mu+U)
$$
再考虑温度项：
$$
\partial_Tf_0=f_0(1-f_0)\times\frac{-\epsilon+\mu}{k_B^2T^2}\\
\partial_Tf_0\dot r\cdot\nabla T=\frac{1}{k_BT}f_0(1-f_0)\dot r\cdot\frac{-\epsilon+\mu}{k_B}\nabla \ln T
$$

-------------------

综上，方程可以表示为：
$$
\beta  v\cdot \left\{\nabla(\mu + U)-\frac{\epsilon-\mu}{k_B}\nabla\ln T \right\}-\frac{e}{\hbar}\frac{\partial f_1}{\partial k}\cdot (v\times B)=\xi
$$
其中，
$$
\beta = \frac{1}{k_BT}f_0(1-f_0)=-\frac{1}{k_BT}\partial_\epsilon f_0
$$
磁感应强度也可以替换为矢量势：
$$
v\times(\nabla\times A)=\nabla(v\cdot A)-A(\nabla\cdot v)=\nabla(v\cdot A)
$$

----------------------------

下面讨论碰撞项的弛豫时间近似模型。碰撞导致了轨道间的跃迁。注意到无碰撞的后果是轨道不出现交叉，因而各个轨道附近的粒子数密度保持恒定，即：
$$
\frac{\text{d} f}{\text{d} t}=0
$$
当我们关注某个单电子，其与系统中其他粒子的两次碰撞之间的间隔时间，即为弛豫时间。弛豫时间越短，电子与系统的作用越剧烈，则系统恢复平衡态的速度越快，准粒子寿命越短。**弛豫时间近似**假设了如下情况：
$$
\frac{\text{d} f}{\text{d} t}=-\frac{f-f_0}{\tau}
$$
负号表示偏离随时间的增加而减小($f-f_0>0$)。当粒子在相空间保持静止时（即$k,r$不依赖于时间，进而$f_0$不依赖于时间），上式的解为：
$$
f=f_1(t=0)e^{-t/\tau}+f_0
$$

------------------

弛豫时间近似下，电场的作用可以通过解Bolzmann方程得到：
$$
\beta v\cdot\nabla U=-\frac{f-f_0}{\tau}
$$

$$
-\frac{1}{k_BT}\tau f_0(1-f_0) v\cdot \nabla U+f_0=f
$$

或者用最初的形式：
$$
\frac{e}{\hbar}E\cdot\partial_kf_0=\frac{f-f_0}{\tau}
$$
注意到：
$$
\Delta f=\nabla f\cdot\text{d} l=f(l)-f(l+\text{d} l)
$$
且$f-f_0=f_1$已经假设为小量（因而$e\tau E/\hbar$也必须是小量），故：
$$
f(k)=f_0(k+\frac{e\tau}{\hbar}E)
$$
即，电场的作用是令Fermi Sphere的中心出现微小的移动。

-----------------------

考虑在$\vec k$空间对函数$\psi(\vec k)$的求和：
$$
\sum_k \psi(k),k=lK_j/N_j,l\in \mathbb Z,-N_j<l<N_j
$$

其中，因子2源于自旋简并，即，已经假设$\psi_\uparrow=\psi_\downarrow$。
$$
\frac{2}{\Delta \vec k}\sum_k \psi(\vec k)\Delta \vec k=\frac{V}{4\pi^3}\int\psi(\vec k)\text{d} {\vec{k}}
$$

其中，$\Delta k$是倒格子原胞的$1/N(N\equiv N_1N_2N_3)$。$N$是总的原胞数目，是$10^{23}$量级，因而对$k$的求和采用连续化近似是相当合理的：
$$
\Delta k=\Omega^*/N=(2\pi)^3/(\Omega N)=8\pi^3/V
$$
其中，$\Omega,\Omega^*$为正格子和倒格子的原胞体积，$V$为晶体的总体积。

--------------------------------------

一种常用的积分方法。首先注意到等能面可以遍历整个1stBZ，否则意味着有些电子态没有确定的能量。并且等能面只会遍历一次1stBZ，否则那些重复遍历的位置的电子态将具有多个能量，对于同一条能带上的电子而言，这是不允许的。因而我们总可以先对某个等能面积分，再对所有允许的能量积分。注意到$\text{d} \epsilon$并不是$\vec k $空间中的单位线元，即，如果取一个沿着$\nabla_k \epsilon $方向的线元$\text{d} l$，有$\text{d} \epsilon/\text{d} l\neq 1$。因而需要归一化。选取线元$\text{d} {\vec {l}}$，则：
$$
\text{d} \epsilon=\nabla_k\epsilon\cdot\text{d}{\vec l}=\abs{\nabla_k\epsilon}\text{d} l
$$
其中，$\text{d} l$已经取为沿着能量梯度方向的一段线元。综上，当处理函数$\psi(\epsilon(\vec k))$形式的函数时，总可以做如下变换：
$$
\begin{align}
\int \psi(\epsilon(\vec k))\text{d}{\vec k}
&=\int\text{d} \epsilon\int_{S(\epsilon)}\text{d} a\frac{\psi(\epsilon(\vec k))}{\abs{\nabla_k \epsilon}}
\end{align}
$$
注意引入的归一化因子$1/\abs{\nabla_k\epsilon}$，用于使$\text{d} \epsilon$归一化为$\vec k$空间中的单位线元。

通过上述步骤可以允许我们通过能带的色散关系导出态密度（通常提及态密度，默认为能量空间中的电子态密度）的表达式。已知BZ中总的电子态可以直接数$\vec k$空间中的电子态数目，亦可将态密度对能量积分，即：
$$
\sum_k2=\int g_n(\epsilon)\text{d}\epsilon
$$
其中，$n$为带指数，$g_n$为能带$n$的态密度。等式左侧可以化为积分形式：
$$
\sum_k2=\frac{V}{4\pi^3}\int\text{d}{\vec k}=\frac{V}{4\pi^3}\int\text{d}\epsilon\int_{S(\epsilon)}\text{d} a\frac{1}{\abs{\nabla_k\epsilon}}
$$
即，对于某条能带，其态密度为：
$$
g_n(\epsilon)=\frac{V}{4\pi^3}\int_{S(\epsilon)}\frac{\text{d} a}{\abs{\nabla_k\epsilon}}
$$
这也提醒我们，态密度是广延量，当晶体体积越大时，$\vec k$空间中的点子越密集，因而态密度也就随之变大了。

由于$\epsilon(\vec k)$是连续可导的周期函数，根据中值定理，在BZ中必须存在$\nabla_k\epsilon=0$的点。这会导致大多数情况下，低维情况$g_n$发散，三维情况$\text{d}{g_n}/\text{d}{\epsilon}$发散。考虑三维Fermi sphere，即能量色散为各向同性三维抛物面，$\epsilon=\beta k^2$，则：
$$
\nabla_k\epsilon=2\beta\vec k,\abs{\nabla_k\epsilon}=2\beta k
$$

$$
\begin{align}
g_n(\epsilon)&=\frac{V}{4\pi^3}\int_{k^2=\epsilon/\beta}\text{d} a\frac{1}{2\beta k}\\
&=\frac{V}{4\pi^3}\int_{k^2=\epsilon/\beta}\frac{1}{2\beta k}\times (k^2 \sin\theta \text{d}\phi\text{d}\theta)\\
&=\frac{V}{4\pi^3}\frac{\sqrt{\epsilon/\beta}}{2\beta}\int\sin\theta\text{d}\phi\text{d}\theta\\
&=\frac{V}{4\pi^3}\times4\pi\times\frac{1}{2}\sqrt{\frac{\epsilon}{\beta^3}}\\
&=\frac{V}{2\pi^2\sqrt{\beta^3}}\sqrt{\epsilon}
\end{align}
$$

可见，Fermi sphere的中心是一个态密度的奇点，$\text{d}{g_n}/\text{d}\epsilon\propto\epsilon^{-1/2}$。若将三维抛物面更换为各向异性，则一些情况下可以得到具有拐点的$g_n(\epsilon)$函数。这些奇异点均称之为van Hove 奇异 (Singularity)。它源于晶体的平移对称性，是晶体的本征属性。（因为晶体有了平移对称性，才能够保证$\nabla_k\epsilon=0$的位置必然存在，从而导致发散）

-----------------------------------

电流密度为单位时间内通过单位截面的电荷量，选取$\text{d} V$作为子系统，其电流密度为：
$$
\vec J = \frac{\text{d} V}{4\pi^3}\int(-e\vec v)f\text{d}{\vec k}
$$

已知平衡状态下无电流，即$\int vf_0\text{d}{\vec k}=0$，故：
$$
\begin{align}
\vec J &= \frac{-e\text{d} V}{4\pi^3}\int \vec vf_1\text{d}{\vec k}\\
&=\frac{-e^2\text{d} V}{4\pi^3\hbar}\int \vec v\tau \frac{\partial f_0}{\partial \vec k}\text{d}{\vec k}\cdot \vec E
\end{align}
$$
其中：
$$
\begin{align}
\int \vec v\tau\nabla_kf_0\text{d}{\vec k}&=\int \vec v\tau\partial_\epsilon f_0\frac{\text{d} \epsilon}{\text{d} {\vec k}}\text{d} {\vec k}\\
&=-\int\vec v\tau(-\partial_\epsilon f_0)\hbar\vec v\text{d}{\vec k}\\
&=-\hbar\int\tau\delta(\epsilon-\epsilon_F)\vec v\vec v\text{d}{\vec k}\\
&=-\hbar\int\delta(\epsilon-\epsilon_F)\text{d}\epsilon\int_{S(\epsilon)}\frac{\vec v\vec v}{\abs{\nabla_k\epsilon}}\tau(\vec k)\text{d}{a}\\
&=-\int\delta(\epsilon-\epsilon_F)\left[\int_{S(\epsilon)}\tau(\vec k)\frac{\vec v\vec v}{v}\text{d} a\right]\text{d}\epsilon\\\
&=-\int_{S(\epsilon_F)}\tau(\vec k)\frac{\vec v\vec v}{v}\text{d} a

\end{align}
$$
注意到仅当能量积分范围包含$\epsilon _F$时，上式成立，即上式求出的是**金属**的情况，否则将会得到零，需要考虑更高阶的非平衡分布，如$f_2,f_3$。这也可以解释为什么半导体的电导率远小于金属。综上，金属中的电流密度可以表示为：
$$
\vec J=\left[\frac{e^2\text{d} V}{4\pi^3\hbar}\int_{S(\epsilon_F)}\tau(\vec k)\frac{\vec v \vec v }{v}\text{d} a\right]\cdot\vec E=\hat \sigma\cdot\vec E
$$
电导率为张量：
$$
\hat \sigma=\beta\int_{S(\epsilon_F)}\tau\frac{\vec v\vec v}{v}\text{d} a
$$
其中，$S(\epsilon_F)$即Fermi Surface。下面讨论简单立方对称性对$\hat\sigma$的限制。将其写为矩阵表达式（用$V$来指代$\vec v$的列向量）：
$$
\hat\sigma=\beta\int_{S_F}\frac{\tau}{v}VV^{T}\text{d} a
$$
则其转置为：
$$
\hat\sigma^T=\beta\int_{S_F}\frac{\tau}{v}(VV^T)^T\text{d} a=\hat\sigma
$$
故这是一个对称张量。引入简单立方对称性后，将三个四度对称轴放在$x,y,z$轴上。当立方沿$z$轴旋转$90\degree$时，$x$变为$y$，$y$变为$-x$，$z$不变。根据四度对称性可知：
$$
\sigma_{xy}=\sigma_{y,-x}=\beta\int\frac{\tau}{v}v_yv_{-x}\text{d} a=-\sigma_{yx}\\
\sigma_{xx}=\sigma_{yy}
$$
此处，$v_{-x}=\vec v\cdot(-\hat x)=-v_x$。注意到$\hat\sigma$为对称张量，故有：
$$
\sigma_{xy}=-\sigma_{yx}=-\sigma_{xy}=0
$$
显然，$\hat\sigma$只有三个相等的对角元，其余皆为$0$。显然有：
$$
v_x^2=v_y^2=v_z^2=\frac{1}{3}v^2\\
v=\sqrt{3v_x^2}
$$
$\hat\sigma$可以表示为一个数字：
$$
\sigma=\frac{\beta}{3}\int_{S_F}\tau v\text{d} a=\frac{\beta}{3}\int_{S_F}l(\vec k)\text{d} a
$$
其中，$l$为平均自由程。

--------------------

电声互作用本质上是在绝热近似的基础上引入晶格振动的微扰项。考虑简单晶格情况，晶格周期势在绝热近似下表示为各个离子的库伦势的和：
$$
V_0=\sum_lv(\vec r-\vec l)
$$
其中，$\vec l$为正格矢。引入晶格振动：
$$
\begin{align}
V^\prime&=\sum_l\left\{ 
v(\vec r-\vec l-\vec u_l) - v(\vec r-\vec l)
\right\}\\
&=-\sum_l\left\{
\vec u_l\cdot\nabla v(\vec r-\vec l)
\right\}

\end{align}
$$
已经采用了小位移近似，在简谐近似下，格波表示为：
$$
\vec u_l=\vec A e^{i(\vec q\cdot l-\omega t)}
$$
代入微扰项：
$$
\begin{align}
V^\prime&= -\sum_l\left\{e^{i(\vec q\cdot\vec l-\omega t)}\vec A\cdot \nabla v(\vec r-\vec l)\right\}\\
&=-e^{-i\omega t}\sum_le^{iql}\vec A\cdot \nabla v(\vec r-\vec l)\\
&=e^{-i\omega t}s_q
\end{align}
$$
这是含时微扰项，采用 Fermi’s golden rule 来描述跃迁速率（即单位时间的跃迁概率）：
$$
R(k\rightarrow k')=\frac{2\pi }{\hbar}\delta(\epsilon'-\epsilon-\hbar\omega)
\left| 
\bra{k}s_q\ket{k'}
\right|^2
$$
其中，$\ket{k}$为Bloch态：
$$
\bra{r}\ket{k}=u(\vec r)\exp(i\vec k\cdot\vec r), u(\vec r+\vec l)=u(\vec r)
$$
求解矩阵元：
$$
\begin{align}
\bra{k} s_q\ket{k'}
&=\sum_l\bra{k}e^{iql}\vec A\cdot \nabla v(\vec r-\vec l)\ket{k'}\\
&=\int\text{d} r\int \text{d}{r'}\sum_l\bra{k}\ket{r}\bra{r}e^{iql}A\cdot\partial_rv(r-l)\ket{r'}\bra{r'}\ket{k'}\\
&=\
\int \text{d} r\sum_l u(r)u^*(r)e^{i(k'-k)r}e^{iql}A\cdot\partial_rv(r-l)\\
&=
\int \text{d} r\sum_l u(r+l)u^*(r+l)e^{i(k'-k)(r+l)}e^{iql}A\cdot\partial_rv(r)\\
&=
\int uu^*e^{i(k'-k)r}A\cdot\partial_rv(r)\text{d} r\sum_le^{i(k'-k+q)\cdot l}\\
&=
\bra{k}A\cdot\partial_rv(r)\ket{k'}\delta_{k'-k+q+G_h,0}
\end{align}
$$
这给出了动量守恒要求：
$$
k'-k+q=G_h
$$
不作更精细的讨论。上式表明，可以发射或吸收一个声子，前后的总动量差为一个倒格矢。当倒格矢不为0时，称为U process，否则为N process。

-------------
