---
title: 共形变换~Conformal transformation
date: 2026-05-31
tags: [CFT, 共形场论]
categories: [物理笔记]
math: true
toc: true
---

# 共形变换~Conformal transformation

大致来说，**共形变换**（conformal transformation）是两个空间之间保角但不一定保长的映射。形式化地，考虑可微映射 $\phi: U \to V$，其中 $U, V$ 分别是流形 $M$ 和 $M'$ 的开子集。令 $g$ 和 $g'$ 分别为 $M$ 和 $M'$ 的度规张量。当拉回度规 $\phi^* g'$ 满足以下条件时，称 $\phi$ 为共形变换：

$$\phi^* g' = \Lambda \, g \tag{2.1}$$

若记 $x' = \phi(x)$（$x \in U$），此条件的协变形式为：

$$g'_{\rho\sigma}(x') \frac{\partial x'^\rho}{\partial x^\mu} \frac{\partial x'^\sigma}{\partial x^\nu} = \Lambda(x) \, g_{\mu\nu}(x) \tag{2.2}$$

其中 $\Lambda(x)$ 确保向量之间的夹角在变换下保持不变。

{% alertBlockquote info 一维的特例 %}
在一维中，由于标量度规的性质，任何光滑变换天然是共形的。毕竟一条直线上的变换，绝对不能改变角度。
{% endalertBlockquote %}

从 (2.2) 可以推出，任意两个向量 $V_1'^\mu(x')$ 和 $V_2'^\mu(x')$ 在 $M'$ 中的内积在共形映射下按以下方式缩放：

$$g_{\mu\nu}(x) V_1^\mu(x) V_2^\nu(x) = g'_{\mu\nu}(x') V_1'^\mu(x') V_2'^\nu(x') \, \Lambda \tag{2.3}$$

其中 $V_1^\mu(x)$ 和 $V_2^\mu(x)$ 是拉回向量。此式表明 $M'$ 中两向量之间的夹角在通过共形变换映射到 $M$ 后保持不变。

---

# 共形不变的条件~Conditions for conformal invariance

此后我们聚焦于 $M' = M$ 的情形，即 $g' = g$。取 $M$ 为具有度规 $\eta_{\mu\nu} = \operatorname{diag}(-1, +1, \dots, +1)$ 的平坦空间，共形变换条件简化为：

$$\eta_{\rho\sigma} \frac{\partial x'^\rho}{\partial x^\mu} \frac{\partial x'^\sigma}{\partial x^\nu} = \Lambda(x) \, \eta_{\mu\nu} \tag{2.4}$$
<span id="conformal-condition"></span>

在此变换下，线元变换为：

$$ds^2 = \eta_{\mu\nu} dx^\mu dx^\nu \to \eta_{\rho\sigma} dx'^\rho dx'^\sigma = \eta_{\rho\sigma} \frac{\partial x'^\rho}{\partial x^\mu} \frac{\partial x'^\sigma}{\partial x^\nu} dx^\mu dx^\nu = \Lambda(x) ds^2 \tag{2.5}$$

{% alertBlockquote info 两点注记 %}
1. 两个共形变换的复合仍是共形变换，这意味着**共形变换构成一个群**。
2. 当 $\Lambda(x) = 1$ 时，共形变换退化为 **Poincaré 群**变换（平移、旋转、Lorentz boost），它们同时保角和保长。
{% endalertBlockquote %}

## 无穷小形式

我们设置的无穷小变换 $x'^{\rho}=x^{\rho}+\varepsilon^{\rho}(x)+\mathcal{O}(\varepsilon^{2})$ 此时是形式上的，它应当满足共形变换条件，所以这种描述当然具有规范冗余，我们应当找出它的规范条件，下面将导出 $\varepsilon^{\mu}$ 所应当满足的规范条件，或者说**共形 Killing 方程**：

$$\boxed{\partial_\mu \epsilon_\nu + \partial_\nu \epsilon_\mu = \frac{2}{d} (\partial \cdot \epsilon) \eta_{\mu\nu}} \tag{comfomal killing equation} $$
<span id="conformal-killing-equation"></span>

为找出**平坦空间**中的基本共形变换，先研究无穷小变换：

$$x'^\rho = x^\rho + \epsilon^\rho(x) + O(\epsilon^2) \tag{2.6}$$

其中 $\epsilon(x) \ll 1$。代入[共形条件](#conformal-condition)，保留到 $\epsilon$ 的一阶：

$$\partial_\mu \epsilon_\nu + \partial_\nu \epsilon_\mu = K(x) \, \eta_{\mu\nu} \tag{2.7}$$

其中 $K(x) = \Lambda(x) - 1$ 是某无穷小函数。对 (2.7) 两边求迹（乘以 $\eta^{\mu\nu}$ 缩并）：

$$K(x) = \frac{2}{d} \partial_\mu \epsilon^\mu \tag{2.8}$$

代回 (2.7)，得到仅依赖 $\epsilon(x)$ 的约束——**共形 Killing 方程**：

$$\boxed{\partial_\mu \epsilon_\nu + \partial_\nu \epsilon_\mu = \frac{2}{d} (\partial \cdot \epsilon) \eta_{\mu\nu}} \tag{2.9}$$

## 两个有用的导出方程

**第一式**——对 (2.9) 两边取 $\partial^\nu$：

$$\partial_\mu (\partial \cdot \epsilon) + \Box \epsilon_\mu = \frac{2}{d} \partial_\mu (\partial \cdot \epsilon) \tag{2.10}$$
<span id="2-10"></span>

由此立即可见：**仅在 $d = 2$ 时**，$\Box \epsilon_\mu = 0$——这正是二维共形变换特殊性的一个来源。

再取 $\partial^\nu$，经过指标交换和利用 (2.9)，可得：

$$(\eta_{\mu\nu} \Box + (d-2) \partial_\mu \partial_\nu)(\partial \cdot \epsilon) = 0 \tag{2.13}$$

对时空指标求迹：

$$(d-1) \Box (\partial \cdot \epsilon) = 0 \tag{2.14}$$

**第二式**——对 (2.9) 取 $\partial_\rho$ 并置换指标运算，得到：

$$\boxed{2 \partial_\mu \partial_\nu \epsilon_\rho = \frac{2}{d} \bigl(-\eta_{\mu\nu} \partial_\rho + \eta_{\rho\mu} \partial_\nu + \eta_{\nu\rho} \partial_\mu\bigr)(\partial \cdot \epsilon)} \tag{2.15}$$

{% alertBlockquote tip Summary %}
从无穷小条件 (2.9) 出发：
- **$d=1$**：(2.14) 对 $\epsilon(x)$ 不施加任何约束，任何光滑变换都是共形的
- **$d \geq 3$**：将在下节看到，$\epsilon^\mu$ 最多是 $x^\nu$ 的二次函数，共形变换只有**有限个参数**
- **$d=2$**：将在 2.6 节 看到，$\epsilon(z)$ 是任意全纯函数，共形变换有**无穷维**参数

正是 $d=2$ 的这种无限维对称性，使得 2d CFT 在很大程度上可以被精确求解。
{% endalertBlockquote %}

---

# 高维共形变换~Conformal transformation in $d \geq 3$

## 从方程中解出 $\epsilon^\mu$ 的形式

对于 $d \geq 3$，(2.14) 给出 $\Box (\partial \cdot \epsilon) = 0$。代入 (2.13) 得 $\partial_\mu \partial_\nu (\partial \cdot \epsilon) = 0$，这意味着 **$(\partial \cdot \epsilon)$ 最多是 $x^\mu$ 的线性函数**：

$$\partial \cdot \epsilon = A + B_\mu x^\mu$$

将线性表达式代回 (2.15)，立即得到 $\partial_\mu \partial_\nu \epsilon_\rho$ 等于常数。由此推得 **$\epsilon^\mu$ 最多是 $x^\nu$ 的二次函数**，可设：

$$\epsilon^\mu = a^\mu + b^{\mu\nu} x_\nu + c^{\mu\nu\rho} x_\nu x_\rho \tag{2.16}$$

其中 $c^{\mu\nu\rho} = c^{\mu\rho\nu}$，且所有常数均 $\ll 1$。

## 逐项分析

由于 (2.9) 中各项均只含一个导数，对常数的共形约束应不依赖 $x^\mu$，因此可对 (2.16) 中的各项分别处理。

### 常数项 $a^\mu$——平移

$a^\mu$ 不受 (2.9) 约束，描述**无穷小平移**：

$$x'^\mu = x^\mu + a^\mu$$

其生成元为动量算符：

$$P_\mu = -i \partial_\mu$$
<span id="generator-P"></span>

### 线性项 $b^{\mu\nu}$——缩放与旋转

将线性项代入 (2.9)：

$$b_{\mu\nu} + b_{\nu\mu} = \frac{2}{d} (\eta^{\rho\sigma} b_{\sigma\rho}) \eta_{\mu\nu} \tag{2.18}$$

将 $b_{\mu\nu}$ 分解为对称与反对称部分：$b_{\mu\nu} = n_{\mu\nu} + m_{\mu\nu}$，其中 $n_{\mu\nu} = n_{\nu\mu}$，$m_{\mu\nu} = -m_{\nu\mu}$。

- **反对称部分** $m_{\mu\nu}$ 自动满足 (2.18)，对应无穷小**旋转** $x'^\mu = (\delta^\mu_\nu + m^{\mu}_{\;\,\nu}) x^\nu$，生成元为角动量算符：
  $$L_{\mu\nu} = i (x_\mu \partial_\nu - x_\nu \partial_\mu)$$
  ^generator-L

- **对称部分** 给出约束 $n_{\mu\nu} = \frac{1}{d} (\eta^{\rho\sigma} n_{\sigma\rho}) \eta_{\mu\nu}$，即对称部分必须正比于度规。因此：
  $$b_{\mu\nu} = \alpha \eta_{\mu\nu} + m_{\mu\nu} \tag{2.19}$$
  其中 $\alpha \eta_{\mu\nu}$ 描述无穷小**标度变换** $x'^\mu = (1 + \alpha) x^\mu$，生成元为伸缩算符：
  $$D = -i x^\mu \partial_\mu$$
  ^generator-D

### 二次项 $c^{\mu\nu\rho}$——特殊共形变换 (SCT)

将二次项代入 (2.15)，经过直接计算得到：

$$c^{\mu\nu\rho} = \eta^{\rho\mu} f^\nu + \eta^{\mu\nu} f^\rho - \eta^{\nu\rho} f^\mu \tag{2.20}$$

其中 $f^\mu = \frac{1}{d} c^{\rho}_{\;\,\rho\mu}$。对应的变换为：

$$x'^\mu = x^\mu + 2 (x \cdot f) x^\mu - (x \cdot x) f^\mu \tag{2.21}$$

这称为**特殊共形变换**（Special Conformal Transformation, SCT），生成元为：

$$K_\mu = -i \bigl(2 x_\mu x^\nu \partial_\nu - (x \cdot x) \partial_\mu\bigr)$$
<span id="generator-K"></span>

{% alertBlockquote info 生成元的统一公式 %}
所有生成元可通过定义计算：
$$i G_a \Phi = \frac{\delta x^\mu}{\delta \omega^a} \partial_\mu \Phi \tag{2.17}$$
假设场 $\Phi$ 在参数为 $\omega^a$ 的变换下本身不受影响。
{% endalertBlockquote %}

---

# 有限共形变换~Finite conformal transformation

至此我们已经找到了所有基本的无穷小共形变换及其生成元。为确定共形群，需要找出对应的**有限变换**。

|  变换类型   |                                          有限形式                                           |                                 生成元                                  |
| :-----: | :-------------------------------------------------------------------------------------: | :------------------------------------------------------------------: |
| **平移**  |                                $x'^\mu = x^\mu + a^\mu$                                 |                      $P_\mu = -i \partial_\mu$                       |
| **伸缩**  |                                 $x'^\mu = \alpha x^\mu$                                 |                     $D = -i x^\mu \partial_\mu$                      |
| **旋转**  |                            $x'^\mu = M^\mu_{\;\,\nu} x^\nu$                             |      $L_{\mu\nu} = i (x_\mu \partial_\nu - x_\nu \partial_\mu)$      |
| **SCT** | $x'^\mu = \dfrac{x^\mu - (x \cdot x) f^\mu}{1 - 2(f \cdot x) + (f \cdot f)(x \cdot x)}$ | $K_\mu = -i (2 x_\mu x^\nu \partial_\nu - (x \cdot x) \partial_\mu)$ |
<span id="Finite-conformal-transformation-and-gen"></span>

## SCT 的有限形式推导

SCT 的有限形式可通过以下洞见导出：关于单位球的**反演**（inversion）$x'^\mu = x^\mu / (x \cdot x)$ 也是一个共形映射（但没有无穷小形式，也没有连续参数）。利用共形映射的传递性：

$$\text{SCT} = \text{反演} \circ \text{平移} \circ \text{反演}$$

即先将 $x^\mu$ 反演，平移 $f^\mu$，再反演回去：

$$x^{\mu} \xrightarrow{\text{inversion}} \frac{x^{\mu}}{x\cdot x} \xrightarrow{\text{transform}} \frac{x^{\mu}}{x\cdot x}-f^{\mu} \xrightarrow{\text{inversion}} \frac{x'^{\mu}}{x'\cdot x'} $$
$$x'^\mu = \frac{\frac{x^\mu}{x \cdot x} - f^\mu}{\bigl(\frac{x_\mu}{x \cdot x} - f_\mu\bigr)\bigl(\frac{x^\mu}{x \cdot x} - f^\mu\bigr)} = \frac{x^\mu - (x \cdot x) f^\mu}{1 - 2(f \cdot x) + (f \cdot f)(x \cdot x)} \tag{2.22}$$

{% alertBlockquote info 验证 %}
当 $f^\mu \to 0$ 时，(2.22) 退化为无穷小 SCT (2.21)。
{% endalertBlockquote %}

SCT 的共形因子可通过 [共形条件](#conformal-condition) 算出：

$$\frac{\partial x'^{\mu}}{\partial x^{\rho}} = \frac{\Delta\delta^{\mu}_{\rho} + 2x^{\mu}f_{\rho} - 2f^{\mu}x_{\rho} + 4(f\cdot x)f^{\mu}x_{\rho}-2f^{2}x^{\mu}x_{\rho}-2x^{2}f^{\mu}f_{\rho}}{\Delta^{2}} $$
$$\eta_{\mu \nu} \frac{\partial x'^{\mu}}{\partial x^{\rho}} \frac{\partial x'^{\nu}}{\partial x^{\sigma}} = \Lambda \eta_{\rho \sigma} $$
$$\Lambda(x) = \bigl(1 - 2(f \cdot x) + (f \cdot f)(x \cdot x)\bigr)^{-2} \tag{2.23}$$

注意从 (2.22) 看出，点 $x^\mu = \frac{1}{f \cdot f} f^\mu$ 被映射到无穷远。因此，为定义任意共形变换，**必须包含无穷远点**。这也被称之为**紧致化**。

---

# 共形群和代数~Conformal groups and algebras

$d \geq 3$ 维中的共形变换构成一个群，称为**共形群**（conformal group）。无穷小共形变换生成的代数是该群的 Lie 代数，即**共形代数**（conformal algebra）。

## 代数的维数

由表格中的生成元计数：

$$N = \underbrace{d}_{\text{平移}} + \underbrace{1}_{\text{伸缩}} + \underbrace{\frac{d(d-1)}{2}}_{\text{旋转}} + \underbrace{d}_{\text{SCT}} = \frac{(d+2)(d+1)}{2}$$

## 对易关系

直接计算给出**无中心荷**的对易关系。非平凡的对易子为：

$$\boxed{\begin{align}
[D, P_\mu] &= i P_\mu, \\[4pt]
[D, K_\mu] &= -i K_\mu, \\[4pt]
[K_\mu, P_\nu] &= 2i (\eta_{\mu\nu} D - L_{\mu\nu}), \\[4pt]
[K_\rho, L_{\mu\nu}] &= i (\eta_{\rho\mu} K_\nu - \eta_{\rho\nu} K_\mu), \\[4pt]
[P_\rho, L_{\mu\nu}] &= i (\eta_{\rho\mu} P_\nu - \eta_{\rho\nu} P_\mu), \\[4pt]
[L_{\mu\nu}, L_{\rho\sigma}] &= i (\eta_{\rho\nu} L_{\mu\sigma} + \eta_{\mu\sigma} L_{\nu\rho} - \eta_{\rho\mu} L_{\nu\sigma} - \eta_{\nu\sigma} L_{\mu\rho})
\end{align}} \tag{2.24}$$

其余对易子为零。

## 与 $\mathfrak{so}(1, d+1)$ 的同构

为将对易关系化为更简洁的形式，定义以下生成元：

$$J_{\mu,\nu} = L_{\mu,\nu}, \quad
J_{-1,0} = D, \quad
J_{-1,\mu} = \frac{1}{2}(P_\mu - K_\mu), \quad
J_{0,\mu} = \frac{1}{2}(P_\mu + K_\mu) ,\quad J_{AB}=-J_{BA}$$

利用 (2.24)，可验证 $J_{m,n}$（$m, n = -1, 0, 1, \dots, d$）满足：

$$\boxed{[J_{mn}, J_{rs}] = i (\eta_{ms} J_{nr} + \eta_{nr} J_{ms} - \eta_{mr} J_{ns} - \eta_{ns} J_{mr})} \tag{2.25}$$

{% alertBlockquote tip 核心结论 %}
对于 $d$ 维 Euclidean 空间 $\mathbb{R}^d$，度规为 $\eta_{mn} = \operatorname{diag}(-1, 1, \dots, 1)$，(2.25) 正是 Lie 代数 $\mathfrak{so}(1, d+1)$ 的对易关系。

推广到 $d = p + q \geq 3$ 的空间 $\mathbb{R}^{p,q}$，对应的共形群为 **$\operatorname{SO}(p+1, q+1)$**。
{% endalertBlockquote %}

<details>
<summary>对应关系</summary>

$$\begin{pmatrix} J_{-1,-1} & J_{-1,0} & J_{-1,1} & J_{-1,2} & \dots \\ J_{0,-1} & J_{0,0} & J_{0,1} & J_{0,2} & \dots \\ J_{1,-1} & J_{1,0} & J_{1,1} & J_{1,2} & \dots \\ \dots & \dots & \dots & \dots & \dots \end{pmatrix} $$
$$\begin{pmatrix} 0 & D & \frac{P_{1}-K_{1}}{2} & \frac{P_{2}-K_{2}}{2} & \dots \\ -D & 0 & \frac{P_{1}+K_{1}}{2} & \frac{P_{2}+K_{2}}{2} & \dots \\ -\frac{P_{1}-K_{1}}{2} & -\frac{P_{1}+K_{1}}{2} & 0 & L_{12} & \dots \\ \dots & \dots & \dots & \dots & \dots \end{pmatrix} $$

</details>

---

# 二维共形变换~2d conformal transformation

现在聚焦于 $d=2$ 且具有 Euclidean 度规的特殊情形——这正是 2d CFT 展示出其强大可解性的根本原因所在。

## Cauchy-Riemann 方程

从 [共形条件](#conformal-killing-equation) 或者说 [#2-10](#2-10) 中可以看出，二维中共形变换的无穷小条件为：

$$\partial_1 \epsilon^1 = \partial_2 \epsilon^2, \qquad \partial_1 \epsilon^2 = -\partial_2 \epsilon^1 \tag{2.26}$$

这正是复分析中的 **Cauchy-Riemann 方程**！引入复坐标：

$$z = x^1 + i x^2, \quad \epsilon = \epsilon^1 + i \epsilon^2, \qquad
\bar{z} = x^1 - i x^2, \quad \bar{\epsilon} = \epsilon^1 - i \epsilon^2 \tag{2.27}$$

(2.26) 表明 **$\epsilon(z)$ 是全纯函数**（在某开集内）。等价地，任何无穷小全纯变换 $z' = z + \epsilon(z)$ 都产生一个二维共形变换。

事实上，复平面上的任何全纯函数都是共形的（即保角）。为证明这一点，用复变量重写线元：

$$ds^2 = (dx^1)^2 + (dx^2)^2 = dz \, d\bar{z} \tag{2.28}$$

复坐标下的度规为：

$$g_{\alpha\beta} = \begin{pmatrix} 0 & \frac{1}{2} \\ \frac{1}{2} & 0 \end{pmatrix}, \qquad
g^{\alpha\beta} = \begin{pmatrix} 0 & 2 \\ 2 & 0 \end{pmatrix} \tag{2.29}$$

共形条件 (2.4) 变为：

$$g_{\alpha\beta} \frac{\partial z'^\alpha}{\partial z^\gamma} \frac{\partial z'^\beta}{\partial z^\delta} = \Lambda(z, \bar{z}) \, g_{\gamma\delta} \tag{2.30}$$

当 $z' = f(z)$ 是全纯函数时此条件自动满足，共形因子为：

$$\Lambda(z, \bar{z}) = \left|\frac{\partial f(z)}{\partial z}\right|^2$$

{% alertBlockquote important $d=2$ 的特殊性 %}
在高维 $d \geq 3$ 中，共形 Killing 方程只有有限个线性独立的解（对应有限维共形群 $\operatorname{SO}(d, 2)$）。但在 $d=2$ 中，$\epsilon(z)$ 可以是**任意全纯函数**——这给出了**无穷维**的对称代数。正是这种无限维对称性使得 2d CFT 在很大程度上有望被精确求解。
{% endalertBlockquote %}

## Witt 代数

对 $\epsilon(z)$ 在 $z=0$ 附近做 Laurent 展开，一般的无穷小共形变换可写为：

$$z' = z + \epsilon(z) = z + \sum_{n \in \mathbb{Z}} \epsilon_n (-z^{n+1}), \qquad
\bar{z}' = \bar{z} + \bar{\epsilon}(\bar{z}) = \bar{z} + \sum_{n \in \mathbb{Z}} \bar{\epsilon}_n (-\bar{z}^{n+1})$$

其中 $\epsilon_n$ 和 $\bar{\epsilon}_n$ 是无穷小参数。

<details>
<summary>为什么是 $z=0$ 处的 Laurent 展开？</summary>

这个展开涉及三个问题：为什么 Laurent 而非 Taylor、为什么在 $z=0$ 处、为什么取 $-z^{n+1}$ 这个基底？

**1. 为什么必须是 Laurent 展开（而非 Taylor）？**

$\epsilon(z)$ 是某开集上的全纯函数，但未必在全复平面解析——它可以在 $z=0$（或 $z=\infty$）处有极点。如果只用 Taylor 展开 $\epsilon(z) = \sum_{n \geq 0} c_n z^n$，将丢失所有 $n < 0$ 的负幂项。而这些负幂项对应的生成元 $\ell_n$（$n \leq -2$）和正幂项对应的 $\ell_n$（$n \geq 2$）一样重要——在量子理论中，它们会分别成为 Virasoro 代数的**湮灭算符**和**产生算符**，构成 Fock 空间的基石。只保留 Taylor 展开就等于只保留了一半的代数。

**2. 为什么在 $z=0$ 处展开？**

$z=0$ 是复平面的自然原点。CFT 中通常将"原点"对应于某个算符插入点——例如径向量子化中，$z=0$ 对应 $t = -\infty$ 的渐近过去，$z=\infty$ 对应 $t=+\infty$ 的渐近未来。在 $z=0$ 附近研究 $\epsilon(z)$，就是研究局域共形变换在一点附近如何作用。

如果我们关心的是 $z=a$ 处的局域变换，只需做一个平移 $z \to z-a$ 即可。选择 $z=0$ 是最方便的约定，因为 Laurent 展开的最简形式（以 $z=0$ 为中心）给出最简洁的对易关系，且任何其他点的展开均可通过平移 $(z-a)$ 获得。

**3. 为什么取基底 $-z^{n+1}$？**

可以从两种角度理解：
- **生成元的定义**：我们要找的是无穷小共形变换的生成元——即李导数 $\mathcal{L}_\epsilon$ 作用在场上时的算符。对于变换 $z' = z + \epsilon(z)$，标量场的变分为 $\delta\phi = -\epsilon(z)\partial_z\phi$。若希望将 $\delta\phi$ 写成 $\sum \epsilon_n \ell_n \phi$ 的形式，自然有 $\ell_n \propto -z^{n+1}\partial_z$。符号约定（$-$ 号）纯粹是为了使 Witt 代数对易子 $[\ell_n, \ell_m] = (n-m)\ell_{n+m}$ 不带多余的负号。
- **Witt 代数简洁性**：令 $\ell_n = -z^{n+1}\partial_z$，则 $[\ell_n, \ell_m] = (n-m)\ell_{n+m}$。若换用其他基底（如 $+z^{n+1}\partial_z$ 或 $z^n\partial_z$ 等），对易子会产生额外的符号或偏移因子，增加不必要的复杂性。

**4. 展开背后的物理意义**

Laurent 展开的正负幂次分工有着清晰的物理图像：

| $n$ 范围 | 生成元 | $z=0$ 行为 | $z=\infty$ 行为 | 物理角色 |
|:-------:|:------:|:----------:|:--------------:|:--------|
| $n = -1$ | $\ell_{-1} = -\partial_z$ | 正则 | 正则 | 平移（全局） |
| $n = 0$ | $\ell_0 = -z\partial_z$ | 正则 | 正则 | 伸缩+旋转（全局） |
| $n = +1$ | $\ell_1 = -z^2\partial_z$ | 正则 | 正则 | SCT（全局） |
| $n \leq -2$ | $\ell_n$ | **奇异** | 正则 | 局域"产生"变换 |
| $n \geq 2$ | $\ell_n$ | 正则 | **奇异** | 局域"湮灭"变换 |

正是 Laurent 展开同时包含正、负幂项，才使得我们能完整描述**局域的**（在 $z=0$ 处奇异的）共形变换——这超出了有限维全局共形群 $\operatorname{SL}(2, \mathbb{C})$ 的范畴，是 2d CFT 无穷维对称性的肇因。

</details>

考虑平面上的标量无量纲场 $\phi(z, \bar{z})$，变换效果为 $\phi(z, \bar{z}) \to \phi'(z', \bar{z}') = \phi(z, \bar{z})$，其变分为：

$$\delta\phi \equiv \phi'(z, \bar{z}) - \phi(z, \bar{z}) = -\sum_{n \in \mathbb{Z}} \bigl(\epsilon_n \ell_n \phi(z, \bar{z}) + \bar{\epsilon}_n \bar{\ell}_n \phi(z, \bar{z})\bigr) \tag{2.32}$$

其中引入了生成元：

$$\boxed{\ell_n = -z^{n+1} \partial_z, \qquad \bar{\ell}_n = -\bar{z}^{n+1} \bar{\partial}_{\bar{z}}} \tag{2.33}$$
<span id="witt-gen"></span>

无穷小共形变换的数量是无穷多的。这些局部生成元的对易子可直接计算：

$$\boxed{\begin{align}
[\ell_n, \ell_m] &= (n - m) \ell_{n+m}, \\
[\bar{\ell}_n, \bar{\ell}_m] &= (n - m) \bar{\ell}_{n+m}, \\
[\ell_n, \bar{\ell}_m] &= 0
\end{align}} \tag{2.34}$$
<span id="witt-algebra"></span>

第一个对易关系定义了所谓的 **Witt 代数**。局部共形代数 (2.34) 是两个 Witt 代数的直和——分别对应**全纯部分**和**反全纯部分**。

## Möbius 变换：全局共形变换

二维中的**全局**共形变换定义为在 Riemann 球面 $S^2 \simeq \mathbb{C} \cup \{\infty\}$ 上可逆且良定义的变换。

考虑 Laurent 展开 $\ell_n = -z^{n+1} \partial_z$：

- 在 $z=0$ 处非奇异：仅当 $n \geq -1$
- 在 $z = \infty$ 处（令 $z = -1/w$）：$\ell_n = (-\frac{1}{w})^{n-1} \partial_w$，非奇异仅当 $n \leq 1$

因此，在 Riemann 球面上全局定义的共形变换仅由 $\ell_{-1}, \ell_0, \ell_1$ 生成。这三个生成元构成 Witt 代数 (2.34) 的一个**闭子代数**。

{% alertBlockquote info 全局共形变换的几何意义 %}
利用 $\ell_n = -z^{n+1} \partial_z$：

| 变换 | 生成元 | 无穷小形式 | 有限形式 |
|:----:|:------:|:----------|:---------|
| **平移** | $\ell_{-1} = -\partial_z$ | $z' = z - \epsilon$ | $z \mapsto z + b$ |
| **伸缩 + 旋转** | $\ell_0 = -z \partial_z$ | $z' = a z$ | $z \mapsto a z$ |
| **SCT** | $\ell_1$ | 二次变换 | $z \mapsto \frac{z}{cz + 1}$ |

其中 $b \in \mathbb{C}$，$a$ 的模对应伸缩、辐角对应旋转。可通过换元 $z = re^{i\theta}$ 显见：
$$\ell_0 + \bar{\ell}_0 = -r \partial_r \quad (\text{伸缩}), \qquad i(\ell_0 - \bar{\ell}_0) = -\partial_\theta \quad (\text{旋转}) \tag{2.36}$$

$\ell_1$ 可通过换元 $w = -1/z$ 理解为 $w$ 中的平移 $\ell_1 = -\partial_w$，$w \mapsto w - c$，即 $z \mapsto \frac{z}{cz + 1}$。
{% endalertBlockquote %}
<span id="geo-glo-comformal-transition"></span>

全局共形群 $\{\ell_{-1}, \ell_0, \ell_1\} \oplus \{\bar{\ell}_{-1}, \bar{\ell}_0, \bar{\ell}_1\}$ 正是 **$\operatorname{SL}(2, \mathbb{C}) / \mathbb{Z}_2 \simeq \operatorname{SO}(3, 1)$**，即 $d=2$ 情形的有限维共形群。

<div id="mobius-container"></div>
<script>
var htmlStr = '<div style="width: 100%; max-width: 1040px; margin: 0 auto; font-family: sans-serif; color: var(--text-color, #333);">' +
    '<div style="background: var(--red-5, #ffecec); border: 1px solid var(--red-4, #ffd0d0); padding: 14px; border-radius: 6px; margin-bottom: 14px;">' +
        '<div style="display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px;">' +
            '<div><strong style="color: var(--red-1, #ff5252); font-size: 1.05em;">Möbius 变换：</strong> <span class="mobius-formula-hud" style="font-family: Consolas, monospace; font-size: 1.1em; margin-left: 8px; font-weight: 600;">w = (az+b)/(cz+d)</span></div>' +
            '<div style="font-size: 0.95em;"><span style="color: var(--text-color-dim, #888);">行列式 det(ad - bc)：</span> <span class="mobius-det-hud" style="font-family: Consolas, monospace; font-weight: 700; color: #52c41a;">1.000 + 0.000i</span></div>' +
        '</div>' +
    '</div>' +
    '<div style="display: flex; gap: 16px; width: 100%; margin-bottom: 14px; flex-wrap: wrap;">' +
        '<div style="flex: 1; min-width: 320px; background: var(--red-6, #fff7f7); border: 1px solid var(--red-4, #ffd0d0); border-radius: 6px; padding: 10px;">' +
            '<div style="text-align: center; margin-bottom: 6px; font-weight: 600; font-size: 0.9em; color: var(--text-color-dim, #888); letter-spacing: 0.5px;">z 平面（参考网格）</div>' +
            '<canvas class="mobiusLeftCanvas" style="width:300px;height:300px;display:block;border-radius:4px"></canvas>' +
        '</div>' +
        '<div style="flex: 1; min-width: 320px; background: var(--red-6, #fff7f7); border: 1px solid var(--red-4, #ffd0d0); border-radius: 6px; padding: 10px;">' +
            '<div style="text-align: center; margin-bottom: 6px; font-weight: 600; font-size: 0.9em; color: var(--text-color-dim, #888); letter-spacing: 0.5px;">w 平面（共形拉回像）</div>' +
            '<canvas class="mobiusRightCanvas" style="width:600px;height:600px;display:block;border-radius:4px"></canvas>' +
        '</div>' +
    '</div>' +
    '<div style="background: var(--red-5, #ffecec); border: 1px solid var(--red-4, #ffd0d0); padding: 14px; border-radius: 6px; margin-bottom: 14px; display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 12px; font-size: 0.85em;">' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Re(a)</span><span class="val-ra" style="font-family:Consolas, monospace;">1.00</span></label><input type="range" class="slide-ra" min="-3" max="3" step="0.01" value="1" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Im(a)</span><span class="val-ia" style="font-family:Consolas, monospace;">0.00</span></label><input type="range" class="slide-ia" min="-3" max="3" step="0.01" value="0" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Re(b)</span><span class="val-rb" style="font-family:Consolas, monospace;">0.00</span></label><input type="range" class="slide-rb" min="-3" max="3" step="0.01" value="0" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Im(b)</span><span class="val-ib" style="font-family:Consolas, monospace;">0.00</span></label><input type="range" class="slide-ib" min="-3" max="3" step="0.01" value="0" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Re(c)</span><span class="val-rc" style="font-family:Consolas, monospace;">0.00</span></label><input type="range" class="slide-rc" min="-3" max="3" step="0.01" value="0" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Im(c)</span><span class="val-ic" style="font-family:Consolas, monospace;">0.00</span></label><input type="range" class="slide-ic" min="-3" max="3" step="0.01" value="0" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Re(d)</span><span class="val-rd" style="font-family:Consolas, monospace;">1.00</span></label><input type="range" class="slide-rd" min="-3" max="3" step="0.01" value="1" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
        '<div><label style="display:flex; justify-content:space-between; margin-bottom:2px; font-weight:600;"><span>Im(d)</span><span class="val-id" style="font-family:Consolas, monospace;">0.00</span></label><input type="range" class="slide-id" min="-3" max="3" step="0.01" value="0" style="width:100%; accent-color: var(--red-1, #ff5252); cursor:pointer;"></div>' +
    '</div>' +
    '<div style="display: flex; flex-wrap: wrap; gap: 8px; justify-content: center; background: var(--red-5, #ffecec); border: 1px solid var(--red-4, #ffd0d0); padding: 10px; border-radius: 6px;">' +
        '<button class="btn-id" style="cursor:pointer; padding: 6px 14px; font-size:0.85em; font-weight:600; background: var(--red-6, #fff7f7); color: var(--text-color, #333); border: 1px solid var(--red-4, #ffd0d0); border-radius: 4px;">恒等变换</button>' +
        '<button class="btn-trans" style="cursor:pointer; padding: 6px 14px; font-size:0.85em; font-weight:600; background: var(--red-6, #fff7f7); color: var(--text-color, #333); border: 1px solid var(--red-4, #ffd0d0); border-radius: 4px;">平移</button>' +
        '<button class="btn-dil" style="cursor:pointer; padding: 6px 14px; font-size:0.85em; font-weight:600; background: var(--red-6, #fff7f7); color: var(--text-color, #333); border: 1px solid var(--red-4, #ffd0d0); border-radius: 4px;">伸缩+旋转</button>' +
        '<button class="btn-inv" style="cursor:pointer; padding: 6px 14px; font-size:0.85em; font-weight:600; background: var(--red-6, #fff7f7); color: var(--text-color, #333); border: 1px solid var(--red-4, #ffd0d0); border-radius: 4px;">反演 (z → -1/z)</button>' +
        '<button class="btn-sct" style="cursor:pointer; padding: 6px 14px; font-size:0.85em; font-weight:600; background: var(--red-6, #fff7f7); color: var(--text-color, #333); border: 1px solid var(--red-4, #ffd0d0); border-radius: 4px;">SCT</button>' +
        '<button class="btn-gen" style="cursor:pointer; padding: 6px 14px; font-size:0.85em; font-weight:600; background: var(--red-6, #fff7f7); color: var(--text-color, #333); border: 1px solid var(--red-4, #ffd0d0); border-radius: 4px;">一般 SL(2,C)</button>' +
    '</div>' +
'</div>';
(function(){ var w=document.getElementById("mobius-document.getElementById("mobius-container")"); if(w) w.innerHTML=htmlStr; })();
setTimeout(function() {
    var canvasLeft = document.getElementById("mobius-container").querySelector(".mobiusLeftCanvas");
    var canvasRight = document.getElementById("mobius-container").querySelector(".mobiusRightCanvas");
    if (!canvasLeft || !canvasRight) return;
    var ctxLeft = canvasLeft.getContext("2d");
    var ctxRight = canvasRight.getContext("2d");
    var currentDoc = canvasLeft.ownerDocument;
    var currentWindow = currentDoc.defaultView || window;
    var dpr = currentWindow.devicePixelRatio || 1;
    var W = 600, H = 600;
    canvasLeft.width = W * dpr; canvasLeft.height = H * dpr; ctxLeft.scale(dpr, dpr);
    canvasRight.width = W * dpr; canvasRight.height = H * dpr; ctxRight.scale(dpr, dpr);

    var hudFormula = document.getElementById("mobius-container").querySelector(".mobius-formula-hud");
    var hudDet = document.getElementById("mobius-container").querySelector(".mobius-det-hud");
    var sliderRa = document.getElementById("mobius-container").querySelector(".slide-ra"), valRa = document.getElementById("mobius-container").querySelector(".val-ra");
    var sliderIa = document.getElementById("mobius-container").querySelector(".slide-ia"), valIa = document.getElementById("mobius-container").querySelector(".val-ia");
    var sliderRb = document.getElementById("mobius-container").querySelector(".slide-rb"), valRb = document.getElementById("mobius-container").querySelector(".val-rb");
    var sliderIb = document.getElementById("mobius-container").querySelector(".slide-ib"), valIb = document.getElementById("mobius-container").querySelector(".val-ib");
    var sliderRc = document.getElementById("mobius-container").querySelector(".slide-rc"), valRc = document.getElementById("mobius-container").querySelector(".val-rc");
    var sliderIc = document.getElementById("mobius-container").querySelector(".slide-ic"), valIc = document.getElementById("mobius-container").querySelector(".val-ic");
    var sliderRd = document.getElementById("mobius-container").querySelector(".slide-rd"), val_rd = document.getElementById("mobius-container").querySelector(".val-rd");
    var sliderId = document.getElementById("mobius-container").querySelector(".slide-id"), valId = document.getElementById("mobius-container").querySelector(".val-id");

    var state = { ar: 1.0, ai: 0.0, br: 0.0, bi: 0.0, cr: 0.0, ci: 0.0, dr: 1.0, di: 0.0 };
    var target = { ar: 1.0, ai: 0.0, br: 0.0, bi: 0.0, cr: 0.0, ci: 0.0, dr: 1.0, di: 0.0 };

    var presets = {
        identity: { ar: 1.0, ai: 0.0, br: 0.0, bi: 0.0, cr: 0.0, ci: 0.0, dr: 1.0, di: 0.0 },
        translation: { ar: 1.0, ai: 0.0, br: 1.0, bi: 0.5, cr: 0.0, ci: 0.0, dr: 1.0, di: 0.0 },
        dilatation: { ar: 1.2990, ai: 0.75, br: 0.0, bi: 0.0, cr: 0.0, ci: 0.0, dr: 0.5774, di: -0.3333 },
        inversion: { ar: 0.0, ai: 0.0, br: -1.0, bi: 0.0, cr: 1.0, ci: 0.0, dr: 0.0, di: 0.0 },
        sct: { ar: 1.0, ai: 0.0, br: 0.0, bi: 0.0, cr: 0.3, ci: 0.0, dr: 1.0, di: 0.0 },
        general: { ar: 0.8528, ai: 0.0, br: 0.4264, bi: 0.0, cr: 0.2132, ci: 0.0, dr: 1.2792, di: 0.0 }
    };

    function updateFromSliders() {
        target.ar = state.ar = parseFloat(sliderRa.value); target.ai = state.ai = parseFloat(sliderIa.value);
        target.br = state.br = parseFloat(sliderRb.value); target.bi = state.bi = parseFloat(sliderIb.value);
        target.cr = state.cr = parseFloat(sliderRc.value); target.ci = state.ci = parseFloat(sliderIc.value);
        target.dr = state.dr = parseFloat(sliderRd.value); target.di = state.di = parseFloat(sliderId.value);
    }
    [sliderRa,sliderIa,sliderRb,sliderIb,sliderRc,sliderIc,sliderRd,sliderId].forEach(function(el){el.addEventListener("input",updateFromSliders)});
    function triggerPreset(p) { target.ar=p.ar;target.ai=p.ai;target.br=p.br;target.bi=p.bi;target.cr=p.cr;target.ci=p.ci;target.dr=p.dr;target.di=p.di; }
    document.getElementById("mobius-container").querySelector(".btn-id").addEventListener("click",function(){triggerPreset(presets.identity)});
    document.getElementById("mobius-container").querySelector(".btn-trans").addEventListener("click",function(){triggerPreset(presets.translation)});
    document.getElementById("mobius-container").querySelector(".btn-dil").addEventListener("click",function(){triggerPreset(presets.dilatation)});
    document.getElementById("mobius-container").querySelector(".btn-inv").addEventListener("click",function(){triggerPreset(presets.inversion)});
    document.getElementById("mobius-container").querySelector(".btn-sct").addEventListener("click",function(){triggerPreset(presets.sct)});
    document.getElementById("mobius-container").querySelector(".btn-gen").addEventListener("click",function(){triggerPreset(presets.general)});

    function formatComplex(r,i){var s=i>=0?"+":"-";return "("+r.toFixed(2)+s+Math.abs(i).toFixed(2)+"i)"}
    function parseColor(css,fb){if(!css)return fb;var c=css.trim();if(c.startsWith("#")){var h=c.substring(1);if(h.length===3)h=h[0]+h[0]+h[1]+h[1]+h[2]+h[2];return[parseInt(h.substring(0,2),16),parseInt(h.substring(2,4),16),parseInt(h.substring(4,6),16)]}if(c.startsWith("rgb")){var m=c.match(/\d+/g);if(m&&m.length>=3)return[parseInt(m[0]),parseInt(m[1]),parseInt(m[2])]}return fb}

    var animationId;
    function draw(){
        if(!canvasLeft.ownerDocument.body.contains(canvasLeft)){cancelAnimationFrame(animationId);return}
        var keys=["ar","ai","br","bi","cr","ci","dr","di"];
        keys.forEach(function(k){state[k]+=(target[k]-state[k])*0.12});
        sliderRa.value=state.ar;valRa.textContent=state.ar.toFixed(2);
        sliderIa.value=state.ai;valIa.textContent=state.ai.toFixed(2);
        sliderRb.value=state.br;valRb.textContent=state.br.toFixed(2);
        sliderIb.value=state.bi;valIb.textContent=state.bi.toFixed(2);
        sliderRc.value=state.cr;valRc.textContent=state.cr.toFixed(2);
        sliderIc.value=state.ci;valIc.textContent=state.ci.toFixed(2);
        sliderRd.value=state.dr;val_rd.textContent=state.dr.toFixed(2);
        sliderId.value=state.di;valId.textContent=state.di.toFixed(2);
        hudFormula.textContent="w = ["+formatComplex(state.ar,state.ai)+"z + "+formatComplex(state.br,state.bi)+"] / ["+formatComplex(state.cr,state.ci)+"z + "+formatComplex(state.dr,state.di)+"]";
        var detRe=(state.ar*state.dr-state.ai*state.di)-(state.br*state.cr-state.bi*state.ci);
        var detIm=(state.ar*state.di+state.ai*state.dr)-(state.br*state.ci+state.bi*state.cr);
        hudDet.textContent=detRe.toFixed(3)+(detIm>=0?" + ":" - ")+Math.abs(detIm).toFixed(3)+"i";

        var bodyStyle=currentWindow.getComputedStyle(currentDoc.body);
        var colorBg=bodyStyle.getPropertyValue('--background-primary').trim()||'#1e1e1e';
        var colorBorder=bodyStyle.getPropertyValue('--background-modifier-border').trim()||'#333';
        var colorText=bodyStyle.getPropertyValue('--text-normal').trim()||'#fff';
        var colorMuted=bodyStyle.getPropertyValue('--text-muted').trim()||'#888';
        var colorAccent=bodyStyle.getPropertyValue('--interactive-accent').trim()||'#07a';
        var cBg=parseColor(colorBg,[25,25,25]),cGrid=parseColor(colorBorder,[55,55,55]);
        var cText=parseColor(colorText,[230,230,230]),cAccent=parseColor(colorAccent,[0,122,204]);

        // Left: z-plane grid
        ctxLeft.fillStyle=colorBg;ctxLeft.fillRect(0,0,W,H);
        ctxLeft.lineWidth=1;ctxLeft.strokeStyle=colorBorder;
        for(var g=-3.0;g<=3.0;g+=0.5){var pos=300+g*100;ctxLeft.beginPath();ctxLeft.moveTo(pos,0);ctxLeft.lineTo(pos,H);ctxLeft.stroke();ctxLeft.beginPath();ctxLeft.moveTo(0,pos);ctxLeft.lineTo(W,pos);ctxLeft.stroke()}
        ctxLeft.lineWidth=1.75;ctxLeft.strokeStyle=colorText;ctxLeft.beginPath();ctxLeft.moveTo(0,300);ctxLeft.lineTo(W,300);ctxLeft.stroke();ctxLeft.beginPath();ctxLeft.moveTo(250,0);ctxLeft.lineTo(250,H);ctxLeft.stroke();
        ctxLeft.lineWidth=3.5;ctxLeft.strokeStyle=colorAccent;ctxLeft.beginPath();ctxLeft.arc(400,250,80,0,2*Math.PI);ctxLeft.stroke();
        ctxLeft.fillStyle=colorMuted;ctxLeft.font="11px Consolas, monospace";ctxLeft.fillText("Re(z)",W-45,292);ctxLeft.fillText("Im(z)",308,18);

        // Right: w-plane pullback via inverse Möbius
        var imgData=ctxRight.createImageData(W,H),buf=imgData.data;
        var ar=state.ar,ai=state.ai,br=state.br,bi=state.bi,cr=state.cr,ci=state.ci,dr=state.dr,di=state.di;
        var idx=0;
        for(var py=0;py<H;py++){var wi=3.0-6.0*py/H;
            for(var px=0;px<W;px++){var wr=-3.0+6.0*px/W;
                var numR=(dr*wr-di*wi)-br,numI=(dr*wi+di*wr)-bi;
                var denR=ar-(cr*wr-ci*wi),denI=ai-(cr*wi+ci*wr);
                var msq=denR*denR+denI*denI;
                if(msq<1e-6){buf[idx]=cBg[0];buf[idx+1]=cBg[1];buf[idx+2]=cBg[2];buf[idx+3]=255;idx+=4;continue}
                var zr=(numR*denR+numI*denI)/msq,zi=(numI*denR-numR*denI)/msq;
                var dr2=zr-1.0,di2=zi-0.5,cd=Math.sqrt(dr2*dr2+di2*di2);
                if(Math.abs(cd-0.8)<0.038){buf[idx]=cAccent[0];buf[idx+1]=cAccent[1];buf[idx+2]=cAccent[2];buf[idx+3]=255}
                else if(Math.abs(zr)<0.035||Math.abs(zi)<0.035){buf[idx]=cText[0];buf[idx+1]=cText[1];buf[idx+2]=cText[2];buf[idx+3]=255}
                else{var rr=zr-Math.round(zr*2)*0.5,ri=zi-Math.round(zi*2)*0.5;
                    if((zr>=-3.05&&zr<=3.05&&Math.abs(rr)<0.02)||(zi>=-3.05&&zi<=3.05&&Math.abs(ri)<0.02)){buf[idx]=cGrid[0];buf[idx+1]=cGrid[1];buf[idx+2]=cGrid[2];buf[idx+3]=255}
                    else{buf[idx]=cBg[0];buf[idx+1]=cBg[1];buf[idx+2]=cBg[2];buf[idx+3]=255}}
                idx+=4}}
        ctxRight.putImageData(imgData,0,0);
        ctxRight.fillStyle=colorMuted;ctxRight.font="11px Consolas, monospace";ctxRight.fillText("Re(w)",W-45,292);ctxRight.fillText("Im(w)",308,18);
        animationId=requestAnimationFrame(draw);
    }
    draw();
}, 50);
</script>

但 2d CFT 的真正威力在于**局域的无穷维 Witt 代数**——以及其中心扩张后得到的 Virasoro 代数。

{% alertBlockquote tip 本章总结 %}
本章从共形变换的几何定义出发，导出了共形 Killing 方程，并分别讨论了 $d \geq 3$ 和 $d=2$ 两种情形：
- **$d \geq 3$**：共形群是有限维 Lie 群 $\operatorname{SO}(d, 2)$，包含平移、旋转、伸缩和 SCT
- **$d=2$**：共形对称性是**无穷维**的，由 Witt 代数 $\oplus$ Witt 代数生成，这是 2d CFT 可解性的根本来源

下一章 Basics in conformal field theory 将在这些对称性基础上引入 Noether 定理、Ward-Takahashi 恒等式、初级场和 Virasoro 代数。
{% endalertBlockquote %}
