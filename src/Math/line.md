本文介绍计算几何中常用的直线方程和直线性质。下面用圆括号(x,y)表示点的坐标，用方括号[x,y]表示方向矢量。

##一、平面直线

### 1. 两点式

过两点$(x_a,y_a)$和$(x_b,y_b)$的直线方程是：
$$ x(y_a-y_b) + y(x_b-x_a) + x_ay_b - x_by_a = 0 $$

### 2.点向式

过点$(x_0,y_0)$且平行于$[l_x,l_y]$的直线方程是：
$$ l_yx - l_xy + l_xy_0 - l_yx_0 = 0 $$

### 3.点法式

过点$(x_0,y_0)$且垂直于$[n_x,n_y]$的直线方程可由$[ l_x,l_y]=[-n_y,n_x]$得到：
$$ n_xx + n_yy - n_xx_0 - n_yy_0 = 0 $$

### 4.角距式

设法向的方向角为 θ，原点到直线的距离为 ρ。由点法式可推出直线方程为：
$$ x\cos θ + y\sin θ = ρ$$

### 5.一般式

上述直线方程都可以写成一般式：
$$ Ax+By+C=0 $$

### 6.参数方程

过点$(x_0,y_0)$，倾角 α 为直线方程为：

$$
\begin{cases}
x=x_0 + \cosα\ t \\
y=y_0 + \sinα\ t
\end{cases}
$$

## 二、直线性质

### 1.点到直线的距离

点$(x_0,y_0)$到直线的距离为：
$$ d = \frac {|Ax_0+By_0+C|}{\sqrt{A^2+B^2}}$$

两条平行线$ Ax+By+C_1=0 $和$ Ax+By+C_2=0 $的距离为：
$$ d = \frac {|C_1-C_2|}{\sqrt{A^2+B^2}}$$

所以$ Ax+By+C=0 $可以看作是过原点的直线$ Ax+By=0 $平移了$ d = \frac {|C|}{\sqrt{A^2+B^2}}$，并且垂直于点(A,B)和原点之间的连线。

### 2.归一化

取$a=\frac{A}{\sqrt{A^2+B^2}}, b=\frac {B}{\sqrt{A^2+B^2}}, c=\frac {C}{\sqrt{A^2+B^2}}$，可得归一化的一般式方程：
$$ ax+by+c=0 $$
点$(x_0,y_0)$到直线的距离为：
$$ d = |ax_0+by_0+c|$$

### 3.两条直线的夹角

两条直线$ A_1x+B_1y+C_1=0 $和$ A_2x+B_2y+C_2=0 $的倾角分别为α和β，夹角θ=α-β的计算方法如下：
$$ tan(α-β) = \frac{tanα - tanβ}{1 + tanα\cdot tanβ} = \frac{A_2B_1-A_1B_2}{A_1A_2+B_1B_2}=\frac{|\vec{l_1}|\cdot|\vec{l_2}|sinθ}{|\vec{l_1}|\cdot|\vec{l_2}|cosθ}=tanθ $$

### 4.直线的交点

将两个直线方程联立，得到一个方程组：

$$
\begin{cases}
A_1x+B_1y+C_1=0 \\
A_2x+B_2y+C_2=0
\end{cases}
$$

可以解出交点坐标为：$x=\frac{B_1C_2-B_2C_1}{A_1B_2-A_2B_1}$, $y=\frac{A_2C_1-A_1C_2}{A_1B_2-A_2B_1}$.
当$A_1B_2-A_2B_1=0$时，两条直线平行，或者说交点在无穷远处。

### 5.点到直线的垂足

联立直线 ax+by+c=0 和过点(m,n)的垂线：

$$
\begin{cases}
ax+by+c=0 \\
bx-ay-bm+an=0
\end{cases}
$$

可得垂足坐标为：$(\frac{b^2m-abn-ac}{a^2+b^2}, \frac{a^2n-abm-bc}{a^2+b^2})$

### 6. 点关于直线的对称点

点(m,n)到关于直线 ax+by+c=0 的对称点的有向距离为$d =\frac{2(am+bn+c)}{\sqrt{a^2+b^2}}$，连线的单位方向为$[\frac{a}{\sqrt{a^2+b^2}}, \frac{b}{\sqrt{a^2+b^2}}]$.
对称点坐标为$(m-\frac{2a(am+bn+c)}{a^2+b^2}, n-\frac{2b(am+bn+c)}{a^2+b^2})$.

### 7.拟合直线

给定 n 个点，拟合一条直线使得这些点到该直线的距离平方和最小。

#### 7.1 直接线性变换法，最小化代数距离

假设直线的系数为(a,b,c)，将点的坐标代入可以得到一组线性方程：

$$
\begin{gathered}
ax_1 + by_1 + c = 0 \\
ax_2 + by_2 + c = 0 \\
... \\
ax_n + by_n + c = 0
\end{gathered}
$$

写成矩阵形式为：

$$
\begin{bmatrix}
   x_1 & y_1 & 1 \\
   x_2 & y_2 & 1 \\
   | & | & | & \\
   x_n & y_n & 1 \\
\end{bmatrix}
\begin{bmatrix}
   a \\ b \\ c
\end{bmatrix}=Av=0
$$

当点的个数 ≤3 时，可以求矩阵 A 的零向量得到拟合的直线；
当点的个数>3 时，可以求$A^TA$的最小本征值对应的本征向量作为拟合的结果。

直接线性变换法的本质是在 3 维空间拟合一个过原点的平面 ax+by+cz=0，使得样本点(xᵢ,yᵢ,1)投影到该平面法线方向上的长度平方和 ∑(axᵢ+byᵢ+c)² 最小，拟合的直线为该平面与 z=1 平面的交线，所以并不能最小化点到直线的距离平方和。

#### 7.2 最小二乘法，最小化点到直线的竖直距离

设 y=ax+b，最小化 S(a,b)=∑(axᵢ+b-yᵢ)²。
写成矩阵形式为：

$$
\begin{bmatrix}
   x_1 & 1 \\
   x_2 & 1 \\
   | & | & \\
   x_n & 1 \\
\end{bmatrix}
\begin{bmatrix}
   a \\ b
\end{bmatrix}=\begin{bmatrix}
   y_1 \\ y_2 \\ | \\ y_n
\end{bmatrix}
$$

记为 $Av=u$.

用最小二乘法可得$v=(A^TA)^{-1}A^Tu$.

还有一种推导是用偏微分求极值：

$$
\begin{aligned}
&\frac{\partial}{\partial b}S=2∑(axᵢ+b-yᵢ)=0 \implies b=\frac{1}{n}(∑yᵢ-a∑xᵢ)\\
&\implies b=\bar{y}-a\bar{x} \\
&\frac{\partial}{\partial a}S=2∑(axᵢ+b-yᵢ)xᵢ=0 \implies ∑(axᵢ+\bar{y}-a\bar{x}-yᵢ) = 0 \\
&\implies a=\frac{∑(yᵢ-\bar{y})xᵢ}{∑(xᵢ-\bar{x})xᵢ} \\
&=\frac{∑(xᵢyᵢ-n\bar{x}\bar{y})}{(∑xᵢ^2)-n\bar{x}^2}=\frac{(∑xᵢyᵢ)-2n\bar{x}\bar{y}+n\bar{x}\bar{y}}{(∑xᵢ^2)-2n\bar{x}\bar{x}+n\bar{x}^2}\\
&=\frac{∑xᵢyᵢ-∑xᵢ\bar{y}-∑\bar{x}yᵢ+∑\bar{x}\bar{y}}{∑xᵢ^2-2∑xᵢ\bar{x}+∑\bar{x}^2}\\
&\implies a=\frac{∑(xᵢ-\bar{x})(yᵢ-\bar{y})}{∑(xᵢ-\bar{x})^2}
\end{aligned}
$$

最小二乘法最小化 y 坐标到直线的竖直距离的平方和，且不适用于 x=c 的直线。

#### 7.3 主成分分析法，最小化点到直线的垂直距离

先计算 n 个点的中心点的坐标（x₀,y₀），即 x 坐标和 y 坐标的平均值。
各个点到中心点的差值组成一个矩阵：

$$
A=\begin{bmatrix}
   x_1-x_0 & y_1-y_0 \\
   x_2-x_0 & y_2-y_0 \\
   | & | & \\
   x_n-x_0 & y_n-y_0 \\
\end{bmatrix}
$$

计算 $S=\dfrac{A^TA}{n-1}$
求 S 的本征值和本征向量，最大的本征值对应的本征向量就是拟合直线的方向，即“主成分”。另一个本征向量的方向垂直于直线方向，使得点到直线的垂直距离和最小，同时这个较小的本征值就等于点到直线的距离的方差。
根据拟合直线的方向和中心点坐标，可求出直线的方程系数。

### 8. 线性组合

两条直线$ a_1x+b_1y+c_1=0 $和$ a_2x+b_2y+c_2=0 $的线性组合：

$$
(λa_1+(1-λ)a_2)x + (λb_1+(1-λ)b_2)y +(λc_1+(1-λ)c_2) = 0
$$

是通过这两条直线的交点的一簇直线。

两个点$(x_1,y_1),(x_2,y_2)$的线性组合$(λx_1+(1-λ)x_2, λy_1+(1-λ)y_2)$是过这两点的直线上的点。

## 三、空间直线

### 1. 两点式

经过点 a 和 b 的直线为：$x=a+λ(b-a)$

### 2. 两向式

直线方向为 m，过原点和直线的平面法向为 n，直线方程为：$ x \times m = n$

### 3. 点向式

过点 a，方向为 n 的直线为：$x=a+λn$

### 4. 点到直线的距离

点 b 到直线$x=a+λn$距离是 b-a 与 n 组成平行四边形，以 n 为底求高：

$$
d = \frac{|(b-a) \times n|}{|n|}
$$

### 5. 两条直线的距离

两条异面直线$x=a+λp$和$x=b+µq$最短距离是三个向量组成的平行六面体的高：

$$
d = \frac{1}{|p \times q|}\det\begin{bmatrix}
   b-a \\ p \\ q
\end{bmatrix}
$$

距离最近处的连线同时垂直与这两条直线，所以

$$
\begin{gathered}
(a+λp - b-µq) \cdot p= 0 \\
(a+λp - b-µq) \cdot q= 0
\end{gathered}
\implies
\begin{gathered}
λp \cdot p - µq \cdot p = (b-a) \cdot p \\
λp \cdot q - µq \cdot q= (b-a) \cdot q
\end{gathered}
$$

解出 λ 和 µ，就可以得到两条直线上距离最近的两个点。
