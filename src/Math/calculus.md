# 微积分 calculus

Calculus is one of the pillars of modern science.

The secret in understanding calculus lies in knowing which quantities may be neglected and which may not.

turning point
inflection point
asymptote 渐近线
secant line 割线
catenary 悬链线

A cable suspended from two towers is in the shape of a catenary, but when a horizontal roadway is suspended from the cable, the cable takes the shape of a parabola.

Constant Function: $$f(x) = b$$
Identity Function: $$f(x) = x$$
Reciprocal Function: $$f(x) = \frac{1}{x}$$
Square Function: $$f(x) = x²$$
Cube Function: $$f(x) = x³$$
Square Root Function: $$f(x) = \sqrt x$$
Cube Root Function: $$f(x) = \sqrt[3]{x}$$
Absolute Value Function: $$f(x) = |x|$$
Greatest Integer Function: $$f(x) = ⌈x⌉$$
Exponential Function: $$f(x)=Ca^x, a>0, a≠1, C≠0$$
The exponential function: $$f(x)=e^x$$
Logarithmic function: $$f(x) = \log_ax$$
Natural logarithm function: $$f(x) = \ln x$$
Common logarithm function: $$f(x) = \lg x$$
Logistic model: $$f(x) = \frac{c}{1+ae^{-bx}}$$
Sigmoid function: $$f(x) = \frac{1}{1+e^{-x}}$$
Transforms: $$f(x) = af(b(x+c))+d$$
Vertical or Horizontal shifts: $$f(x) = f(x+h)+k$$
Compressing or stretching vertically or horizontally: $$f(x) = af(bx)$$
Periodic function: $$f(x) = f(x+p)$$
Sinusoidal Function: $$f(x) = A\sin(ωx-φ)+B$$

Definitaion of natural constant (Euler number):
$$ e = \underset{n→∞}\lim{(1+\frac{1}{n})^n}$$

#### Convex Set.

A set $C ∈ R^n$ is convex if the line segment jointing any two points in $C$ is still contained in $C$.
That is, if $x, y ∈ C$ then $λx+(1-λ)y∈ C$ for all $λ$ with $0≤λ≤1$.

#### Convex Function.

A function $f: C→R$ is convex if $C$ is a convex set, and for all $x, y ∈ C, 0≤λ≤1$:

$$
f(λx + (1-λ)y) ≤ λf(x) + (1-λ)f(y)
$$

The geometric interpretation is that the line segment between the points $(x, f(x))$ and $(y, f(y))$ should lie above the graph of $f$. $f$ is convex if and only if its Hessian matrix is positive semi-definite.
