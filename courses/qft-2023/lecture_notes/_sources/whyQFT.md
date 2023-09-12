---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# 绪论

## 量子场论简介

量子场论是迄今为止描述基本粒子，如电子，光子，夸克，黑格斯玻色子等的相互作用规律的最成功无理论。不仅如此，量子场论的方法和概念也在如经典和量子引力，凝聚态物理，原子分子物理，宇宙学等物理学的各个分支中获得广泛而重要的应用。从某种意义上说，量子场论是整个现代物理学的理论框架，其重要性不亚于微积分之于经典物理学。这样一个如此成功的理论是从何而来的？发展它的原初动机是什么？它有哪些成功的应用和局限？量子场论作为描述自然界迄今为止最为复杂的理论框架，我们不太可能在一个学期内彻底掌握它，但至少希望经过这一门课的学习，能为同学们打开一扇窗户，也为将来更深入地掌握量子场论的概念和方法，乃至做出有意义的工作奠定基础。

**此讲义漏洞甚多，欢迎同学们指出！**

## 预备知识（持续更新中）

### 自然单位制

由于我们将主要讨论相对论性的量子现象，如无特殊说明，我们将采用粒子物理学家的自然单位制（其实主要是想偷懒）。在自然单位制下，
\begin{equation}
c = \hbar = 1
\end{equation}
在自然单位制下，所有带量纲常数（在不考虑统计力学量的情况下）均可用质量量纲表示。例如：
\begin{gather}
[E] = [Mc^2] = [M]\\
[P] = \left[ \frac{Mv}{\sqrt{1 - v^2/c^2}}\right] = [M]\\
[\text{Length}] = [\hbar/P] = [M^{-1}]\\
[\text{time}] = [\hbar/E] = [M^{-1}]
\end{gather}
牛顿引力常数：
\begin{equation}
[G] = \left[V L M^{-2}\right] = [M M^{-1} M^{-2}] = [M^{-2}]
\end{equation}
其中$V$是势能，$L$是长度。

习惯上我们以电子伏特（eV）作为能量（质量）单位，则一些典型的物理量可以表示为：
\begin{align}
& m_\text{electron} = 5.11 \times 10^5 \text{eV} = 511 \text{KeV} = 0.511 \text{MeV}
\\
&m_\text{proton} = 9.383 \times 10^8 \text{eV} = 938.3 \text{MeV} = 0.9383 \text{GeV}
\\
&m_\text{neutron} = 9.395 \times 10^8 \text{eV} = 939.5 \text{MeV} = 0.9395 \text{GeV}
\\
&m_\text{pion} = 1.395 \times 10^8 \text{eV} = 139.5 \text{MeV} = 0.1395 \text{GeV}
\\
&m_\text{top} = 1.73 \times 10^{11} \text{eV} = 173 \text{GeV}
\\
&m_\text{Higgs} = 1.25 \times 10^{11} \text{eV} = 125 \text{GeV}
\\
&m_\text{sun} = 1.12 \times 10^{66} \text{eV} 
\\
&m_\text{Planck} = \sqrt{\frac{\hbar c}{G}} = 1.22 \times 10^{19} \text{GeV}
\end{align}
自然单位制下的真空介电常数和真空磁导率为：
\begin{equation}
\epsilon_0 = \mu_0 = 1
\end{equation}
量子电动力学中的精细结构常数为：
\begin{equation}
\alpha = \frac{e^2}{4\pi \epsilon_0 \hbar c} \simeq \frac{1}{137}
\end{equation}
其中$e$为电子电荷。

### 狭义相对论约定

四维逆变矢量：
\begin{align}
x^\mu = (t, \vec{x}) = (x^0, x^1, x^2, x^3) \\
p^\mu = (E, \vec{p}) = (p^0, p^1, p^2, p^3)
\end{align}

$x$和$y$两点间的洛伦兹不变间隔（应用爱因斯坦求和约定）：
\begin{equation}
\Delta s^2 = \eta_{\mu\nu} (x - y)^\mu (x - y)^\nu = (x^0 - y^0)^2 - (\vec{x} - \vec{y})^2
\end{equation}
其中$\eta_{\mu\nu}$为闵氏空间中的度规张量：
\begin{equation}
\eta_{\mu\nu} = \text{diag}(1, -1, -1, -1)
\end{equation}
在这个度规约定下，
\begin{equation}
\Delta s^2 = \left\{ 
  \begin{array}{ll}
    > 0 & \text{time-like，类时间隔} \\
    = 0 & \text{light-like，类光间隔} \\
    < 0 & \text{space-like，类空间隔}
\end{array}
\right.
\end{equation}
闵氏空间度规的逆定义为：
\begin{equation}
\eta_{\mu\nu} \eta^{\nu \rho} = \delta_\mu^\rho
\end{equation}
可以验证：
\begin{equation}
\eta^{\mu\nu} = \text{diag}(1, -1, -1, -1)
\end{equation}
利用度规张量可以实现洛伦兹指标升降：
\begin{equation}
x_\mu = \eta_{\mu\nu} x^\nu = (x^0, -x^1, -x^2, -x^3) = (x_0, x_1, x_2, x_3)
\end{equation}
其中$x_\mu$称为协变矢量。

洛伦兹变换定义为保间隔不变的坐标变换：
\begin{equation}
x^\mu \mapsto x'^\mu = \Lambda^\mu_{\ \ \nu} x^\nu
\end{equation}
其中$\Lambda^\mu_{\ \ \nu}$为洛伦兹变换矩阵，它的逆写作$(\Lambda^\mu_{\ \ \nu})^{-1} \equiv \Lambda_\mu^{\ \ \nu}$。
由间隔不变的定义：
\begin{equation}
x^2  = \eta_{\mu\nu} x^\mu x^\nu \mapsto \eta_{\mu\nu} x'^\mu x'^\nu = \eta_{\mu\nu} \Lambda^\mu_{\ \ \rho} \Lambda^\nu_{\ \ \sigma} x^\rho x^\sigma = \eta_{\rho\sigma} x^\rho x^\sigma
\end{equation}
得到洛伦兹变换矩阵定义式：
\begin{equation}
\boxed{\eta_{\mu\nu} \Lambda^\mu_{\ \ \rho} \Lambda^\nu_{\ \ \sigma} = \eta_{\rho\sigma}}
\end{equation}
同时间隔不变也给出逆变矢量在洛伦兹变换下的变换规则：
\begin{equation}
x_\mu \mapsto x'_\mu = \Lambda_\mu^{\ \ \nu} x_\nu
\end{equation}
对洛伦兹变换矩阵定义式两边乘以$\Lambda_{\alpha}^{\ \ \rho} \Lambda_{\beta}^{\ \ \sigma}$，得到：
\begin{equation}
\boxed{\eta_{\alpha\beta} = \Lambda_{\alpha}^{\ \ \rho} \Lambda_{\beta}^{\ \ \sigma} \eta_{\rho\sigma}}
\end{equation}
因此，闵氏度规是洛伦兹不变张量。

两个洛伦兹矢量的内积记为：
\begin{equation}
a \cdot b = a^\mu b_\mu = a_\mu b^\mu
\end{equation}
四维导数：
\begin{equation}
\partial_\mu = \frac{\partial}{\partial x^\mu} = \left(\frac{\partial}{\partial t}, \nabla\right)
\end{equation}
其中$\nabla$为三维梯度算符。
\begin{equation}
\partial^\mu = \frac{\partial}{\partial x_\mu} = \left(\frac{\partial}{\partial t}, -\nabla\right)
\end{equation}
四维导数的洛伦兹变换规则：
\begin{equation}
\partial_\mu \mapsto \partial'_\mu = \frac{\partial}{\partial x'^\mu} = \Lambda_\mu^{\ \ \nu} \frac{\partial}{\partial x^\nu} = \Lambda_\mu^{\ \ \nu} \partial_\nu
\end{equation}
因此，四维导数也是洛伦兹矢量。四维达朗伯算符写为
\begin{equation}
\Box = \partial_\mu \partial^\mu = \frac{\partial^2}{\partial t^2} - \nabla^2
\end{equation}

四维Levi-Civita张量记为
\begin{equation}
\epsilon^{\mu\nu\rho\sigma} = \left\{ 
  \begin{array}{ll}
    1 & \text{(0,1,2,3)的偶排列} \\
    -1 & \text{(0,1,2,3)的奇排列} \\
    0 & \text{其它}
\end{array}
\right.
\end{equation}
```{admonition} 作业
- 证明：
\begin{equation*}
\Lambda^\mu_{\ \ \alpha} \Lambda^\nu_{\ \ \beta} \Lambda^\rho_{\ \ \gamma} \Lambda^\sigma_{\ \ \delta} \epsilon^{\alpha\beta\gamma\delta} = \det(\Lambda) \epsilon^{\mu\nu\rho\sigma}
\end{equation*}
其中$\det(\Lambda)$为洛伦兹变换矩阵的行列式。我们将主要关心的是与单位变换连通的$\det(\Lambda) = 1$的情形。
```

## 相对论性量子力学与因果律破坏

既然要讨论相对论性量子力学效应，一个自然想法是将薛定谔方程推广到相对论性的情形。薛定谔方程可以写为
\begin{equation}
i \frac{\partial}{\partial t} |\psi(t) \rangle = H |\psi(t)\rangle
\end{equation}
因此态矢随时间演化通过哈密顿量决定：
\begin{equation}
|\psi(t)\rangle = e^{-iHt} |\psi(0)\rangle
\end{equation}
在非相对论力学中，自由粒子哈密顿量可以通过动量算符写为
\begin{equation}
H = \frac{\boldsymbol{p}^2}{2m} 
\end{equation}
一个平庸的相对论性推广是将$H$写为
\begin{equation}
H = + \sqrt{\boldsymbol{p}^2 + m^2}
\end{equation}
在取根号的时候，另一种选择是取负根，但这时就会碰到所谓的负能态问题。没有太多理由，我们这里很简单地取正根来回避这个问题。虽然哈密顿量被人为写成了正能、与相对论性质能关系相符的形式，但求解这个薛定谔方程出现所谓的因果律破坏疑难。

因果律是狭义相对论的一个重要部分。对于类空间隔的两个事件$O_1$和$O_2$，满足$(\boldsymbol{x}_1 - \boldsymbol{x}_2)^2 > t^2$，因此即使是光信号也无法在两个事件之间传递信息。类空间隔可以用如下图的闵氏时空图示意：
```{figure} figs/lightcone.png
---
height: 450px
name: lightcone of $O_1$
---
```

设想在$T=0$时刻，一个粒子位于$\boldsymbol{x} = 0$：
\begin{equation}
|\psi(0)\rangle = | \boldsymbol{x} =  0 \rangle
\end{equation}
在$t$时刻，我们问这个粒子是否能到达其自身在零时刻的光锥之外。这可通过计算粒子从$\boldsymbol{x} = 0$到$\boldsymbol{x} = \boldsymbol{r}$的概率幅来判断：
\begin{equation}
{\cal A} = \langle \boldsymbol{r} |\psi(t) \rangle = \langle \boldsymbol{r} | e^{-i H t} |\psi(0)\rangle
\end{equation}
其中$|\boldsymbol{r}\rangle$是位置本征态。我们可以将$|\boldsymbol{r}\rangle$展开为动量本征态的叠加：
\begin{equation}
|\boldsymbol{r}\rangle = \int d^3 p  \langle \boldsymbol{r} | \boldsymbol{p} \rangle |\boldsymbol{r} \rangle = \int \frac{d^3 p}{(2\pi)^{3/2}} e^{i \boldsymbol{p} \cdot \boldsymbol{r}} |\boldsymbol{p}\rangle
\end{equation}
代入概率幅公式中，得到
\begin{equation}
{\cal A} = \int \frac{d^3 p}{(2\pi)^3} e^{i \boldsymbol{p} \cdot \boldsymbol{r}} e^{-i \omega_p t}
\end{equation}
其中
\begin{equation}
\omega_p = \sqrt{\boldsymbol{p}^2 + m^2}
\end{equation}
在球极坐标下，令$\boldsymbol{p} \cdot \boldsymbol{r} = p r \cos\theta$，
\begin{align}
{\cal A} &= \int_0^\infty \frac{p^2 dp}{(2\pi)^3} \int_{-1}^1 d \cos\theta \int_0^{2\pi} d\phi \ e^{i p r \cos\theta} e^{-i \omega_p t} \\
&= \int_0^\infty \frac{p^2 dp}{(2 \pi)^2} \frac{1}{ipr} \left( e^{i p r} - e^{-i p r} \right) e^{-i \omega_p t} \\
&= \int_{-\infty}^{\infty} \frac{p dp}{(2 \pi)^2} \frac{1}{ir} e^{ipr} e^{-i \sqrt{\boldsymbol{p}^2 + m^2} t}
\end{align}
到了这一步，情况变得有点复杂。实际上，${\cal A}$本身是发散的，应看成一个分布。我们作一个简化，让$m=0$，这时积分变为
\begin{equation}
{\cal A} = \int_{-\infty}^{\infty} \frac{p dp}{(2 \pi)^2} \frac{1}{ir} e^{-i p (t - r)} = \frac{1}{2 \pi r} \delta'(t - r)
\end{equation}
其中$\delta'(x)$是delta函数的导数。delta函数本身应从分布的意义上理解，其导数也同样。因此，我们看到在零质量极限下，${\cal A}$是一个分布（distribution）而非普通函数，其支点在$t = r$光锥上。

下面我们来看质量非零的情况。对于一个分布，我们可以引入一个正规化参数使其成为一个普通函数。这里，我们可以让$t \to t - i \epsilon$，其中$\epsilon$是一个正实数，在$\epsilon \to 0$的极限下过渡到对应的分布。这时概率幅写为
\begin{equation}
{\cal A} = \int_{-\infty}^{\infty} \frac{p dp}{(2 \pi)^2} \frac{1}{ir} e^{i p  r} e^{-i \sqrt{\boldsymbol{p}^2 + m^2} t - \epsilon \sqrt{\boldsymbol{p}^2 + m^2}}
\end{equation}
将$p$解析延拓到整个复平面，被积函数具有形式
\begin{equation}
F(p) e^{ipr - i \sqrt{p^2 + m^2} t}
\end{equation}
$\lim_{p \to \pm \infty}F(p) = \lim_{p \to \pm \infty} p e^{-\epsilon \sqrt{p^2 + m^2}} \to 0$。借助复变函数中的约当引理，可以将对$p$的积分解析延拓到上半平面，并忽略大圆弧的贡献，仅留下沿割线两岸的贡献，如下图所示。
```{figure} figs/contour_naive.png
---
height: 450px
name: 积分围道
---
```

沿着割线两岸的积分可以写作：
\begin{equation}
{\cal A} = \frac{i}{(2 \pi)^2 r} \int_m^\infty z dz\ e^{-zr} \Big[ e^{t \sqrt{z^2 - m^2}} - e^{- t \sqrt{z^2 - m^2}} \Big]
\end{equation}
注意到对任何$r>t$，即在光锥之外，被积函数是正定的，因此积分结果也必然非零。这告诉我们对哈密顿量所作的简单相对论性修改无法满足因果律的要求，必须引入新的理论形式。

上面积分的计算过程中引入$t - i \epsilon$的过程也许会让人困惑。为了更好看清这个手续是合法的，我们引用这个积分的封闭解：
\begin{equation}
{\cal A} = \frac{m^2}{2 \pi^2} \frac{t}{i \tau^2} K_2(i m \tau)
\end{equation}
其中
\begin{equation}
  \tau = \lim_{\epsilon \to 0_+} \sqrt{(t - i \epsilon)^2 - r^2}
\end{equation}
$K_2(z)$是第二类贝塞尔函数。在$\tau = 0$，即在光锥上，这个结果必须解释成分布，而在光锥之外，它的行为是良定义函数。我们关心的主要是类空间隔的信号传播，在这个区域$\epsilon \to 0$的极限是光滑的。[^ack1]

[^ack1]: 此处感谢与陈豪同学的讨论。
