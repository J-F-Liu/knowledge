# 三角学 trigonometry

在实域内，三角函数的值可以通过单位圆上点的坐标值及相关的线段长度来定义，三角函数又称圆函数。

![circle function](images/circle-function.png)

[正弦和余弦的函数图像](https://www.desmos.com/calculator/ogvpbi5v7j)

#### 余角和补角

$$
\begin{gathered}
\sin(-θ) = -\sinθ, \quad \cos(-θ) = \cosθ \\
\sin(\frac{\pi}{2}-θ) = \cosθ, \quad \cos(\frac{\pi}{2}-θ) = \sinθ \\
\sin(\pi-θ) = sinθ, \quad \cos(\pi-θ) = -\cosθ \\
\tan(\frac{\pi}{2}-θ)=\cot θ, \quad \cot(\frac{\pi}{2}-θ)=\tan θ
\end{gathered}
$$

#### 和角公式

$$
\begin{gathered}
sin(α+β) = sinα \cdot cosβ + cosα \cdot sinβ \\
cos(α+β) = cosα \cdot cosβ - sinα \cdot sinβ \\
tan(α+β) = \frac{tanα + tanβ}{1 - tanα\cdot tanβ}
\end{gathered}
$$

#### 差角公式

$$
\begin{gathered}
sin(α-β) = sinα \cdot cosβ - cosα \cdot sinβ \\
cos(α-β) = cosα \cdot cosβ + sinα \cdot sinβ \\
tan(α-β) = \frac{tanα - tanβ}{1 + tanα\cdot tanβ}
\end{gathered}
$$

tan(α-β)可用于求两条直线的夹角。

#### 倍角公式

$$
\begin{gathered}
sin2α = 2sinα \cdot cosα \\
cos2α = cos^2α - sin^2α = 1 - 2sin^2α = 2cos^2α - 1
\end{gathered}
$$

$$
\begin{gathered}
sin 3α = sin(2α + α) = sin2αcosα+cos2αsinα\\
= 2sinα cos^2α + cos^2αsinα - sin^3α  \\
= 3 sinα cos^2 α − sin^3 α = 3 sinα − 4 sin^3 α
\end{gathered}
$$

#### 半角公式

$$
\begin{gathered}
sin\frac{α}{2} = \pm \sqrt{\frac{1-cosα}{2}} \\
cos\frac{α}{2} = \pm \sqrt{\frac{1+cosα}{2}} \\
tan\frac{α}{2} = \dfrac{sinα}{cosα+1}
\end{gathered}
$$

#### 三倍角公式

$$
sin3x = 3sinx - 4sin^3x
$$

$$
cos3x = 4cos^3x - 3cosx
$$

#### 余弦定理

$$
c^2=a^2+b^2-2abcosγ \quad or \quad cosγ=\frac{a^2+b^2-c^2}{2ab}
$$

#### 正弦定理

$$
\frac{sinα}{a}=\frac{sinβ}{b}=\frac{sinγ}{c}=\frac{1}{2R}=\frac{2A}{abc} \quad or \quad
\begin{gathered}
a = 2Rsinα \\
b = 2Rsinβ \\
c = 2Rsinγ
\end{gathered}
$$

R 是三角形的外接圆半径, A 是三角形的面积.

$$
sin^2 α + sin^2 β − sin^2 γ = 2 sinα sin β cos γ
$$

#### 三角形面积

$$
A = \frac{1}{2}absinγ = \frac{abc}{4R} = 2R^2sinα sinβ sinγ = \frac{a+b+c}{2}\cdot ρ
$$

ρ 是三角形的内切圆半径.

结合海伦公式:
$$ ρ = \sqrt{\frac{(s-a)(s-b)(s-c)}{s}} $$

### 反三角函数

$ sin(arccos(x)) = \sqrt{1-x^2} $

$ cos(arcsin(x)) = \sqrt{1-x^2} $

$ tan(arcsin(x)) = \dfrac{x}{\sqrt{1-x^2}} $

$ tan(arccos(x)) = \dfrac{\sqrt{1-x^2}}{x} $

$ sin(arctan(x)) = \dfrac{x}{\sqrt{1+x^2}} $

$ cos(arctan(x)) = \dfrac{1}{\sqrt{1+x^2}} $

## 微积分 calculus

$ \frac{d}{dx}\sin x = \cos x $

$ \frac{d}{dx}\cos x = -\sin x $

## 双曲函数

- 基本定义

双曲函数的值也可通过双曲线和角终边上的双曲函数线的长度定义。

$$
\begin{gathered}
\sinh x = \cfrac{e^x-e^{-x}}{2} \\
\cosh x = \cfrac{e^x+e^{-x}}{2} \\
\tanh x = \cfrac{\sinh x}{\cosh x} = \cfrac{e^x-e^{-x}}{e^x+e^{-x}} \\
\end{gathered}
$$

- 与三角函数的关系

$$
\begin{gathered}
\sinh (iφ) = i\sin(φ) \\
\cosh (iφ) = \cos(φ) \\
\tanh (iφ) = i\tan(φ) \\
\end{gathered}
$$

- 恒等式、倍角公式

$$
\begin{gathered}
\cosh^2 x - \sinh^2 x = 1 \\
\sinh 2x = 2 \sinh x \cosh x \\
\cosh 2x = \cosh^2x + \sinh^2x = 1 + 2\sinh^2x = 2\cosh^2x - 1 \\
\sinh 3x = 4\sinh^3 x + 3\sinh x \\
\cosh 3x = 4\cosh^3x - 3\cosh x
\end{gathered}
$$

- 应用

悬链线的方程为双曲余弦函数，定义$a$为悬链线系数，悬链线方程为：

$$
y = a \cosh (\frac{x}{a}-1)
$$
