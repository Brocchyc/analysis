---
title: 数学分析1——隐函数定理及动力系统初步
date: 2021-07-11 13:06:00
tags: analysis
mathjax: true
---
## 隐函数定理
### 压缩映像原理
完备度量空间 $X$ 及映射 $f:X\rightarrow X$ ，若 $f$ 是压缩映射，即：
$$
\exist 0<c<1\quad\forall x,y\in X\quad s.t.\quad d(f(x),f(y))\leq c\cdot d(x,y) 
$$
则 $f$ 有唯一不动点 $x_0$

### 反函数定理 
映射 $f：\mathbb{R}^m\rightarrow \mathbb{R}^n\quad s.t.\quad f(x_0)=y_0$ 在 $x_0$ 邻域内连续可微且在 $x_0$ 处Jacobi矩阵非异，则 $\exist y_0$ 邻域，$f$ 在其上有连续可微反函数 $g(y)=x$

证明：

存在性：不妨 $x_0=0\quad y_0=0\quad f'(x_0)=I_m$

令 $y=f(x)=x+\phi(x)$ 则 $\phi(0)=0\quad \phi'(0)=0$

考虑 $y_0$ 小邻域（闭邻域）内的函数空间，其上范数
$$
||\psi(y)|| \triangleq \max_{y}|\psi(y)|
$$
由一致收敛的Cauchy收敛准则，这是一个完备度量空间

定义其上算子
$$
(A\psi)(y)\triangleq -\phi(y+\psi(y))
$$
证明 $A\psi$ 是压缩映射：

$$
\begin{aligned}
    ||A\psi_1-A\psi_2||&=\max_y|\phi(y+\psi_2(y))-\phi(y+\psi_1(y))|\\
    &\leq \max_y \frac{1}{2} |\psi_1(y)-\psi_2(y)|\\
    &=\frac{1}{2}||\psi_1-\psi_2||
\end{aligned}
$$

由压缩映像原理 $y_0$ 邻域存在唯一的 $\psi \quad s.t.\quad A\psi=\psi \Leftrightarrow g(y)=y+\psi(y) \quad s.t.\quad gf=I_m$

可微性: 在 $x_0$ 小邻域内取 $x\quad f(x)=y\quad f(x+h)=y+k$ 则 $g(y)=x\quad g(y+k)=x+h$
 
 记 $f'(x)=T$  
 $$
 \begin{aligned}
     &g(y+k)-g(y)-T^{-1}k=T^{-1}(Th-(f(x+h)-f(x)))\\
&\Rightarrow \left\lvert\frac{g(y+k)-g(y)-T^{-1}k}{k}\right\rvert
=
\left\lvert\frac{T^{-1}(Th-(f(x+h)-f(x)))}{k}\right\rvert\\
&\leq \frac{\lVert T^{-1}\rVert}{\lambda}\cdot \left\lvert\frac{Th-(f(x+h)-f(x))}{k}\right\rvert
 \end{aligned}
 $$
 其中 $\lambda$ 是 $f'$ 在小邻域内算子范数的最小值，即证可微性。

 ### 隐函数定理
 映射 $f:\mathbb{R}^n\times \mathbb{R}^m\rightarrow \mathbb{R}^m\quad f(x_0,y_0)=0$ 且 $f$ 在 $(x_0,y_0)$ 小邻域内连续可微， $D_yf(x_0,y_0)$非异
 
 则在 $x_0$ 小邻域上满足 $f(x,y)=0$ 的 $y$ 表示成 $x$ 的连续可微函数 $y=\phi(x)$， 即：$f(x,\phi(x))=0$

 证明：定义函数 $F:\mathbb{R}^n\times\mathbb{R}^m\rightarrow \mathbb{R}^n\times \mathbb{R}^m$ 如下：
 $$F(x,y)\triangleq (x,f(x,y))$$
 则有 
 $$
 DF = \begin{pmatrix}I_n&\\D_xf&D_yf\end{pmatrix}
 $$
 显见 $DF$ 在 $(x_0,y_0)$ 处非异

 对 $F$ 在 $(x_0,y_0)$ 处应用反函数定理得到:
 $$
 G(x,f(x,y))=(x,y)
 $$
 由
 $$
 G(x,0)=(x,y)
 $$
 即得 $y$ 关于 $x$ 的显式表示。

 ## 动力系统初步
作为压缩映像原理的又一应用，证明动力系统解的存在唯一性定理。
### 动力系统解的存在唯一性定理
$$
\begin{cases}
    \dot{x}=v(x,t)\\
    x_0=\xi 
\end{cases}
$$
$v$ 在某个小邻域上连续可微，则动力系统局部存在唯一的解 $x=\phi(t)$

证明：将微分方程转化为积分方程：
$$
\phi(t)=x_0+\int_{t_0}^t\!v(\phi(\tau),\tau)\,\mathrm{d}\tau
$$
定义算子：
$$
A\phi\triangleq x_0+\int_{t_0}^t\!v(\phi(\tau),\tau)\,\mathrm{d}\tau
$$
证明 $A\phi$ 是压缩映射：
$$
\begin{aligned}
    ||A\phi_1-A\phi_2||
    &\leq\int_{t_0}^t\!|v(\phi_1(\tau),\tau)-v(\phi_2(\tau),\tau)|\,\mathrm{d}\tau\\
    &\leq L\int_{t_0}^t|\phi_1(\tau)-\phi_2(\tau)|\mathrm{d}\tau\\
    &\leq L\alpha||\phi_1-\phi_2||
\end{aligned}
$$
其中 $L$ 是 $\dfrac{\partial v}{\partial x}$ 模长最大值，$\alpha$ 是 $(t,x)\ \text{邻域中}\, |t-t_0|$ 最大值。可选取充分小的邻域使 $L\alpha <1$

