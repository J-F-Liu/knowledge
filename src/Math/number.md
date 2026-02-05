# 运算

对数的发明使得数字的乘除计算变成加减法和查对数表，大大减少了数学家、天文学家的计算量。

# 数论

勾股数
https://www.desmos.com/calculator/nurf0njskd

# 算术基本定理，又称为正整数的唯一分解定理.

> 每个大于 1 的自然数均可写为质数的积，而且这些素因子按大小排列之后，写法仅有一种方式。

例如: 6936=2^3×3×17^2，1200=2^4×3×5^2。

## 分解质因子算法

Naive and slow but simplest (check all numbers from 1 to n):

```python
>>> def factors(n):
      return [i for i in range(1, n + 1) if not n%i]
```

Slightly better (realize that there are no factors between n/2 and n):

```python
>>> def factors(n):
      return [i for i in range(1, n//2 + 1) if not n%i] + [n]

>>> factors(45)
[1, 3, 5, 9, 15, 45]
```

Much better (realize that factors come in pairs, the smaller of which is no bigger than sqrt(n)):

```python
>>> from math import sqrt
>>> def factor(n):
      factors = set()
      for x in range(1, int(sqrt(n)) + 1):
        if n % x == 0:
          factors.add(x)
          factors.add(n//x)
      return sorted(factors)

>>> for i in (45, 53, 64): print( "%i: factors: %s" % (i, factor(i)) )

45: factors: [1, 3, 5, 9, 15, 45]
53: factors: [1, 53]
64: factors: [1, 2, 4, 8, 16, 32, 64]
```

More efficient when factoring many numbers:

```python
from itertools import chain, cycle, accumulate # last of which is Python 3 only

def factors(n):
    def prime_powers(n):
        # c goes through 2, 3, 5, then the infinite (6n+1, 6n+5) series
        for c in accumulate(chain([2, 1, 2], cycle([2,4]))):
            if c*c > n: break
            if n%c: continue
            d,p = (), c
            while not n%c:
                n,p,d = n//c, p*c, d + (p,)
            yield(d)
        if n > 1: yield((n,))

    r = [1]
    for e in prime_powers(n):
        r += [a*b for a in r for b in e]
    return r
```

### 模 p 剩余类域

整数除以素数 p 后得到的余数的集合 {0, 1, 2, ..., p-1}。
加法、乘法做完后都要 “模 p” 取余数。
$$
(a+b)^p = a^p + b^p 
$$
这个在实数中不成立的公式，由于展开式中其他项都含有能被 p 整除的二项式系数而变为 0，竟然奇迹般地成立了！

### p进数

对于一个固定的素数 p，任何一个非零的有理数 a 都可以写成：
$a = p^n * (c/d)$，其中 n 是某个整数，c 和 d 是不能被 p 整除的整数。定义 a 的 p 进绝对值 为：$ |a|_p = p^{-n}$。

一个数能被 p 整除的次数越多，它在 p 进意义下就越 “小”，越接近于 0！



## 实数

实数的特点是小数点后面有无限位小数，这意味着它们包含无限量的信息。
既然我们的世界是有限的，那么它怎么能包含无限的数字和具有无限信息量的数字呢？为了避免这种“有限包含无限”的矛盾，吉辛教授建议回到经典物理学的源头——改变数学语言，这样我们就不必再依赖实数。

在直觉主义数学中，一个命题要么为真，要么为假，要么不确定。量子物理学中也存在随机性。吉辛教授说：“有些人试图不惜一切代价避免随机性，把其他基于实数的变量包括进来。但在我看来，我们不应该试图通过消除随机性来使量子物理学更接近经典物理学。恰恰相反，我们最终必须通过引入不确定性，使经典物理学更接近量子物理学。”

依据实数的概念构建起来的理念世界，相较于现实世界，更简单，却也更强大。
通过理念世界与现实世界之间的映射，可以解释现实世界的现象，指导我们的实践。

完美的圆仅存在于理念的世界中。

若 $a≥0,b≥0$，则：$\sqrt{ab}=\sqrt{a}\sqrt{b}$

## 复数

For a given complex number $z = x+iy$, the real numbers x and y are called the real and imaginary part of z, respectively.
The complex number $\bar z = x − iy$ is called the complex conjugate of z.

Let ϕ denote the angle between the positive x-axis and the ray from the origin through the point (x, y).
This angle, normalised by −π < ϕ ≤ π, is denoted by arg z and called the argument of z.

The non-negative number $|z| = r = \sqrt{x^2 + y^2}$, which is the distance from z to the origin, is called the modulus (or absolute value) of z.

With this notation, we have $z = r (cosϕ + i sin ϕ)$ in polar coordinates.

$$
z · \bar z = (x + iy)(x − iy) = x^2 + y^2 = r^2
$$

###### Euler’s formula.

$$
\begin{gathered}
e^{iϕ} = cosϕ + i sinϕ\\
z = x + iy = r · e^{iϕ}
\end{gathered}
$$

##### n-th roots.

Let z be a complex number with modulus r and argument ϕ. The n-th root of z has the modulus $\sqrt[n]{r}$ and any one of the arguments
$\frac{ϕ}{n}+\frac{2kπ}{n}$, $k = 0, 1, . . . , n−1$.

In particular, for z = 1, the points of roots represent the vertices of a regular n-gon inscribed in the unit
circle.

$$
\begin{gathered}
\sqrt[n]{1} = ε^k = e^\frac{2ki\pi}{n}, k = 0, 1, . . . , n − 1\\
\sum_{k}{ε^k} = 0 \\
ε^m = ε^{m \mod n}
\end{gathered}
$$
