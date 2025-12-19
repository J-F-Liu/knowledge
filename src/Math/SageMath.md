# SageMath

A computer algebra system is a program made to manipulate, simplify and compute mathematical formulas by applying only exact (i.e., symbolic) transformations.

Students will be able to replace pen and paper by keyboard and screen while keeping the same intellectual challenge of understanding mathematics.

### Install

> pacman -S sagemath sagemath-doc jupyter-notebook

### Run

Starts a Sage session in console

> sage

To quit the session enter `quit` and then press ⟨Enter⟩.

To start a Jupyter Notebook instead of a Sage console, run the command

> jupyter notebook --allow-root

vscode 里安装 python 扩展，已集成了 jupyternotebook，不需要额外安装 jupyter 扩展。
新建一个.ipynb 文件，打开它就是 jupyternotebook 的界面了
配置 Jupyter Server 为 SageMath 的本地服务器

## Usage

Basic arithmetic operations

> “four operations”: a+b, a-b, a\*b, a/b
> power: a^b or a\*\*b
> square root: sqrt(a)
> n-th root: a^(1/n)

Integer operations

> integer division: a // b
> remainder: a % b
> quotient and remainder: divmod(a,b)
> factorial n!: factorial(n)
> binomial coefficient: binomial(n,k)

Usual functions on real numbers, complex numbers, ...

> integer part: floor(a)
> absolute value: abs(a)
> elementary functions: sin, cos, ...

Some specials values

> boolean values “true” and “false” True, False
> imaginary unit i: I or i
> infinity ∞: Infinity or oo

Common mathematical constants

> Archimedes’ constant π: pi
> logarithm basis e = exp(1): e
> Euler-Mascheroni constant γ: euler_gamma
> golden ratio ϕ = (1 + √5)/2: golden_ratio
> Catalan’s constant: catalan

Usual mathematical functions

> Exponential and logarithm exp, log
> Logarithm in base a log(x, a)
> Trigonometric functions sin, cos, tan
> Inverse trigonometric functions arcsin, arccos, arctan
> Hyperbolic functions sinh, cosh, tanh
> Inverse hyperbolic functions arcsinh, arccosh, arctanh
> Integer part, etc. floor, ceil, trunc, round
> Square and n-th root sqrt, nth_root

Rewriting trigonometric expressions

> Simplification simplify_trig
> Linearisation reduce_trig
> Anti-linearisation expand_trig

Show approximate value

> numerical_approx(1/e^2)
> numerical_approx(pi, digits=60)

Vector operations

> v = vector([1,2,3]); w = vector([0,5,-9])
> v.cross_product(w)
> v.dot_product(w)

A symbolic expression is a formula and not a value or a mathematical function. The equality test == is not only a syntactic comparison, with `bool(x==y)`, Sage tries to prove that their difference is zero.

Most expressions handled by symbolic computation systems are rational functions, and the expression `a/a` is automatically simplified into 1. This automatic simplification is not compatible with solving equations.

For example, the solution to the equation `ax = a` is `x = a/a`, which is simplified into `x = 1` without distinguishing the special case `a = 0`, for which any scalar x is solution.

Only few simplifications are done automatically. It is possible to explicitly call a simplification function:

```
sage: arccos(sin(pi/3))
arccos(1/2*sqrt(3))
sage: simplify(arccos(sin(pi/3)))
1/6*p
```

The reference manual of each function, constant or command is accessed via the question mark ? after its name:

```
sage: sin?
```

Sage saves the last three results in the special variables `_, __, and ___`.

The symbolic variables should be explicitly declared before being used (SR abbreviates Symbolic Ring), except the symbolic variable x, which is predefined in Sage. The command var(’x’) is a convenient alternative for x = SR.var(’x’).

```
sage: z = SR.var('z')
sage: 2*z + 3
2*z + 3
```

Assigning the symbolic variable `z` to the Python variable `z` is just a convention, which is recommended to avoid confusion.

Sage allows also to define symbolic functions to manipulate expressions. To convert a symbolic expression into a symbolic function, we use either `f(x) = ...`, or the `function` method.

```
sage: y = var('y'); u = sin(x) + x*cos(y)
sage: v = u.function(x, y); v
(x, y) |--> x*cos(y) + sin(x)
sage: w(x, y) = u; w
(x, y) |--> x*cos(y) + sin(x)
```

The `subs` method evaluating an expression by giving a value to some of its parameters.
The `substitute` method replace an expression more complex than a single variable.
The `expand` method is useful to expand polynomials.
The `collect` method groups terms together according to the powers of a
given variable.
There are more: `factor, combine, simplify_rational, partial_fraction`.
The `simplify_full` command applies the methods `simplify_factorial`, `simplify_rectform`, `simplify_trig`, `simplify_rational` and `expand_sum` (in that order).

```
sage: expr = sin(x); expr
sin(x)
sage: expr(x=1)
sin(1)

sage: a, x = var('a, x'); y = cos(x+a) * (x+1); y
(x + 1)*cos(a + x)
sage: y.subs(a=-x); y.subs(x=pi/2, a=pi/3); y.subs(x=0.5, a=2.3)
x + 1
-1/4*sqrt(3)*(pi + 2)
-1.41333351100299

sage: y, z = var('y, z'); f = x^3 + y^2 + z
sage: f.substitute(x^3 == y^2, z==1)
2*y^2 + 1

sage: f(x)=(2*x+1)^3 ; f(-3)
-125
sage: f.expand()
x |--> 8*x^3 + 12*x^2 + 6*x + 1

sage: p = (x+y)*(x+1)^2
sage: p2 = p.expand(); p2
x^3 + x^2*y + 2*x^2 + 2*x*y + x + y
sage: p2.collect(x)
x^3 + x^2*(y + 2) + x*(2*y + 1) + y

sage: ((x+y+sin(x))^2).expand().collect(sin(x))
x^2 + 2*x*y + y^2 + 2*(x + y)*sin(x) + sin(x)^2
```

During a computation, the symbolic variables appearing in expressions are in general considered as taking potentially any value in the complex plane.

The `assume` function, which enables us to define the properties of a variable, which can in turn be reverted by the `forget` instruction.

```
sage: assume(x > 0); bool(sqrt(x^2) == x)
True
sage: forget(x > 0); bool(sqrt(x^2) == x)
False
sage: n = var('n'); assume(n, 'integer'); sin(n*pi)
0
```

```
sage: plot(sin(2*x), x, -pi, pi)
sage: plot3d(sin(pi*sqrt(x^2 + y^2))/sqrt(x^2+y^2),(x,-5,5), (y,-5,5))
sage: sorted(colors)
['aliceblue',
 'antiquewhite',
 'aqua',
 'aquamarine',
 'automatic',
 'azure',
 'beige',
 'bisque',
 'black',
 'blanchedalmond',
 'blue',
 'blueviolet',
 'brown',
 'burlywood',
 'cadetblue',
 'chartreuse',
 'chocolate',
 'coral',
 'cornflowerblue',
 'cornsilk',
 'crimson',
 'cyan',
 'darkblue',
 'darkcyan',
 'darkgoldenrod',
 'darkgray',
 'darkgreen',
 'darkgrey',
 'darkkhaki',
 'darkmagenta',
 'darkolivegreen',
 'darkorange',
 'darkorchid',
 'darkred',
 'darksalmon',
 'darkseagreen',
 'darkslateblue',
 'darkslategray',
 'darkslategrey',
 'darkturquoise',
 'darkviolet',
 'deeppink',
 'deepskyblue',
 'dimgray',
 'dimgrey',
 'dodgerblue',
 'firebrick',
 'floralwhite',
 'forestgreen',
 'fuchsia',
 'gainsboro',
 'ghostwhite',
 'gold',
 'goldenrod',
 'gray',
 'green',
 'greenyellow',
 'grey',
 'honeydew',
 'hotpink',
 'indianred',
 'indigo',
 'ivory',
 'khaki',
 'lavender',
 'lavenderblush',
 'lawngreen',
 'lemonchiffon',
 'lightblue',
 'lightcoral',
 'lightcyan',
 'lightgoldenrodyellow',
 'lightgray',
 'lightgreen',
 'lightgrey',
 'lightpink',
 'lightsalmon',
 'lightseagreen',
 'lightskyblue',
 'lightslategray',
 'lightslategrey',
 'lightsteelblue',
 'lightyellow',
 'lime',
 'limegreen',
 'linen',
 'magenta',
 'maroon',
 'mediumaquamarine',
 'mediumblue',
 'mediumorchid',
 'mediumpurple',
 'mediumseagreen',
 'mediumslateblue',
 'mediumspringgreen',
 'mediumturquoise',
 'mediumvioletred',
 'midnightblue',
 'mintcream',
 'mistyrose',
 'moccasin',
 'navajowhite',
 'navy',
 'oldlace',
 'olive',
 'olivedrab',
 'orange',
 'orangered',
 'orchid',
 'palegoldenrod',
 'palegreen',
 'paleturquoise',
 'palevioletred',
 'papayawhip',
 'peachpuff',
 'peru',
 'pink',
 'plum',
 'powderblue',
 'purple',
 'red',
 'rosybrown',
 'royalblue',
 'saddlebrown',
 'salmon',
 'sandybrown',
 'seagreen',
 'seashell',
 'sienna',
 'silver',
 'skyblue',
 'slateblue',
 'slategray',
 'slategrey',
 'snow',
 'springgreen',
 'steelblue',
 'tan',
 'teal',
 'thistle',
 'tomato',
 'turquoise',
 'violet',
 'wheat',
 'white',
 'whitesmoke',
 'yellow',
 'yellowgreen']
```
var("x,y,z,u,v,w,r,s,t,r_1,r_2,r_3,r_4,r_5,r_6,r_7,r_8,r_9")
def skew_sym(v):
    return matrix([[0,-v[0,2],v[0,1]],[v[0,2],0,-v[0,0]],[-v[0,1],v[0,0],0]])
r1 = matrix([r_1,r_2,r_3])
r2 = matrix([r_4,r_5,r_6])
r3 = matrix([r_7,r_8,r_9])
R = matrix([r1[0],r2[0],r3[0]]).transpose()
f=matrix([x,y,z])
g=matrix([u,v,w])
show(R)
show(skew_sym(f)*skew_sym(f).transpose())

R1=skew_sym(r1)
R2=skew_sym(r2)
R3=skew_sym(r3)

n = skew_sym(f)*R*g.transpose()
N = n*n.transpose()
show(N)

F=f.transpose()*f
G=g.transpose()*g
FF=matrix([[x,y,z,0,0,0,0,0,0],[0,0,0,x,y,z,0,0,0],[0,0,0,0,0,0,x,y,z]])
H=FF.transpose()*G*FF
J=G.tensor_product(F)
show(F)
show(G)
show(H)
show(J)
show(H==J)
RR=block_matrix(1, 3, [R1, R2, R3])
show(RR)
M = RR * H * RR.transpose()
show(expand(M))
show(N==M)

show(R1*G*R2.transpose() == R2*G*R1.transpose())

var("f,s,c_x,c_y")
K=matrix([[f,s,c_x],[0,f,c_y],[0,0,1]])
show(K.inverse())

var("x,y,z,u,v,w")
f=matrix([x,y,1])
g=matrix([u,v,1])
show(f.transpose()*g)
