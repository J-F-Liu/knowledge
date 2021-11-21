# 线性代数 Linear Algebra

The beauty of linear algebra is that many scientific and engineering problems can be modeled using numerical operations on vectors and matrices. Such as:

- quantum mechanics
- machine learning
- computer graphics
- computer vision

An n-tuple of real numbers is called a **point** of $R^n$.

When $n=1,R^1=R$. Geometrically, this is the number line.

When $n=2$, we can think of $R^2$ as the xy-plane.

When $n=3$, we can think of $R^3$ as the space we (appear to) live in.

Extend our intuition for $R^2$ and $R^3$ to $R^n$, they are still “geometric” spaces. This is useful from a psychological standpoint: instead of having n numbers, we are now dealing with just one piece of data.

### 方程组 system of equations

Tons of physical problems boil down to solving systems of linear equations.

non-linear systems of equations can be linearlized proximitly.

We can perform three valid operations on system of equations:

- Scaling: we can multiply both sides of an equation by a nonzero number.
- Replacement: we can add a multiple of one equation to another, replacing the second equation with the result.
- Swap: we can swap two equations.

A system of equations is called inconsistent if it has no solutions. It is called consistent otherwise.

**增广矩阵** augmented matrix

To solve Ax=b, add b as an extra column the matrix A to produce the augmented matrix [A b].

Two matrices are called row equivalent if one can be obtained from the other by doing some number of row operations. So the linear equations of row-equivalent matrices have the same solution set.

**阶梯形矩阵**. A matrix is in row echelon form if:

1. All zero rows are at the bottom.

2. The first nonzero entry of a row is to the right of the first nonzero entry of the row above.

3. Below the first nonzero entry of a row, all entries are zero.

**Definition.** A _pivot_ is the first nonzero entry of a row of a matrix in row echelon form.

**Definition.** A matrix is in _reduced row echelon form_ if it is in row echelon form, and in addition:

4. Each pivot is equal to 1.
5. Each pivot is the only nonzero entry in its column.

If an augmented matrix is in reduced row echelon form, the corresponding linear system is viewed as solved.

**Theorem.** Every matrix is row equivalent to one and only one matrix in reduced row echelon form.

#### Algorithm(Row Reduction)

Step 1a: Swap the 1st row with a lower one so a leftmost nonzero entry is in the 1st row (if necessary).
Step 1b: Scale the 1st row so that its first nonzero entry is equal to 1.
Step 1c: Use row replacement so all entries below this 1 are 0.
Step 2a: Swap the 2nd row with a lower one so that the leftmost nonzero entry is in the 2nd row.
Step 2b: Scale the 2nd row so that its first nonzero entry is equal to 1.
Step 2c: Use row replacement so all entries below this 1 are 0.
Step 3a: Swap the 3rd row with a lower one so that the leftmost nonzero entry is in the 3rd row.
etc.
Last Step: Use row replacement to clear all entries above the pivots, starting with the last pivot.

Definition

A _pivot position_ of a matrix is an entry that is a pivot of a row echelon form of that matrix.

A _pivot column_ of a matrix is a column that contains a pivot position.

An augmented matrix corresponds to an inconsistent system of equations if and only if the last column (i.e., the augmented column) is a _pivot column_.

Definition

Consider a _consistent_ system of equations in the variables $x_1,x_2,...,x_n$. Let A be a row echelon form of the augmented matrix for this system.

We say that $x_i$ is a _free variable_ if its corresponding column in A is _not_ a pivot column.

The _parametric form_ of the solution set of a consistent system of linear equations is obtained by _move all free variables to the right hand side of the equations._

One can think of the free variables as being _independent_ variables, and the non-free variables being _dependent_.

There are three possibilities for the Number of Solutions of a linear system.

1. **_The last column is a pivot column._** In this case, the system is _inconsistent_. There are zero solutions, i.e., the solution set is empty.

2. **_Every column except the last column is a pivot column._** In this case, the system has a _unique_ solution.

3. **_The last column is not a pivot column, and some other column is not a pivot column either._** In this case, the system has _infinitely many_ solutions, corresponding to the infinitely many possible values of the free variable(s).

A linear system with a unique solution has a solution set with one element.
A linear system with no solution has a solution set that is empty. In these cases the solution set is easy to describe.
Solution sets are a challenge to describe only when they contain many elements.

The geometric meaning of Gaussian elimination is turn parallelepiped into a rectangular cuboid for n = 3, whose sides are the three pivots, and the volume does not change.
This volume is called the determinant of the matrix.

To minimize the numeric precision losses, choosing a pivot for accuracy generally boils down to choosing one of the largest (absolute) value elements available.

##### 行列式的性质 Determinant

① 某行(列)加上或减去另一行(列)的几倍，行列式不变。
② 某行(列)乘 k，等于 k 乘此行列式。
③ 互换两行(列)，行列式变号。
④ 两行(列)相同或成比例时，行列式为 0。
⑤ 某行(列)为两项相加减时，行列式可拆成两个行列式相加减。
行列式等于其转置行列式。

$$
det([A_1,kA_2])=k \cdot det([A_1, A_2]) \\
det(kA) = k^ndet(A) \\
det(AB) = det(A) det(B) \\
det([A_1+B_1, A_2])=det([A_1, A_2])+det([B_1, A_2]) \\
det([A_1+B_1, A_2+B_2])=det([A_1, A_2])+det([A_1, B_2])+det([B_1, A_2])+det([B_1, B_2])
$$

### 向量 Vector

A _vector_ is a point in $R^n$, drawn as an arrow. We will usually write it vertically, like a matrix with one column.

An arrow is determined by its length and its direction, not by its location. Unless otherwise specified, we will assume that all vectors start at the origin.

Geometrically, the sum of two vectors v,w is obtained as follows: place the tail of w at the head of v. Then v+w is the vector whose tail is the tail of v and whose head is the head of w. Doing this both ways creates a parallelogram.

Geometrically, the difference of two vectors v,w is obtained as follows: place the tail of v and w at the same point. Then v−w is the vector from the head of w to the head of v.

A scalar multiple of a vector v has the same (or opposite) direction, but a different length.

Scalar product of the vectors a and b:
$$ ⟨a,b⟩ = ⟨a|b⟩ = a · b = \sum_i{a_ib_i} $$

A set of vectors is called orthonormal if its elements are mutually orthogonal and of unit length.

### 线性组合 linear combination

Let $c_1,c_2,...,c_k$ be scalars, and let $v_1,v_2,...,v_k$ be vectors in $R^n$. The vector in $R^n$

$$
c_1v_1+c_2v_2+···+c_kv_k
$$

is called a _linear combination_ of the vectors $v_1,v_2,...,v_k$, with _weights_ or _coefficients_ $c_1,c_2,...,c_k$.

Definition. A vector equation is an equation involving a linear combination of vectors with possibly unknown coefficients.

Asking whether or not a vector equation has a solution is the same as asking if a given vector is a linear combination of some other given vectors. This give us a different, and more geometric, way of viewing systems of linear equations. It lends itself to drawing pictures.

Definition. Let $v_1,v_2,...,v_k$ be vectors in $R^n$. The _span_ of $v_1,v_2,...,v_k$ is the collection of all linear combinations of $v_1,v_2,...,v_k$, and is denoted $Span\{v_1,v_2,...,v_k\}$. In symbols:

$$
Span\{v_1,v_2,...,v_k\}=\{x_1v_1+x_2v_2+···+x_kv_k|x_1,x_2,...,x_k \in R\}
$$

We also say that $Span\{v_1,v_2,...,v_k\}$ is the subset _spanned by_ or _generated by_ the vectors $v_1,v_2,...,v_k$.

The vector equation $x_1v_1+x_2v_2+···+x_kv_k=b$ has a solution is equivalent to say vector $b$ is in the span of $v_1,v_2,...,v_k$.

The span of two noncollinear vectors is the plane containing the origin and the heads of the vectors. Note that three coplanar (but not collinear) vectors span a plane and not a 3-space, just as two collinear vectors span a line and not a plane.

### 矩阵乘法

Let $A$ be an $m×n$ matrix with columns $v_1,v_2,...,v_n$:

$$
A=\begin{bmatrix}
   | & | & & |  \\
   v_1 & v_2 & ... & v_n \\
   | & | & & |
\end{bmatrix}
$$

The _product_ of A with a vector $x$ in $R^n$ is the linear combination of the columns of A:

$$
Ax=x_1v_1+x_2v_2+···+x_nv_n.
$$

This is a vector in $R^m$.

- $A(u+v)=Au+Av$
- $A(cu)=cAu$

### 列空间和行空间

The _column space_ of A is all the vectors $Ax$, wrriten as Col(A).
The columns form a basis of column space.
Similarly, the rows are a basis of row space.

$A=CR$

C is the linear independent columns of A.
R is the reduced row echelon form of A.
C is column basis and R is row basis => Column rank = Row rank.
If A is full rank, C = A and R = I.

There are $n-r$ independent solutions to $Ax=0$.

### 矩阵方程 The Matrix Equation $Ax=b$.

A _matrix equation_ is an equation of the form $Ax=b$, where $A$ is an $m×n$ matrix, $b$ is a vector in $R^m$, and $x$ is a vector whose coefficients $x_1,x_2,...,x_n$ are unknown.

We now have four equivalent ways of writing (and thinking about) a system of linear equations:

- As a system of equations
- As an augmented matrix
- As a vector equation
- As a matrix equation

The matrix equation $Ax=b$ has a solution if and only if $b$ is in the span of the columns of $A$.

#### $Ax=b$的几何图景

行空间：$A_i \cdot x = b_i$，n 个垂直于行向量$A_i$的子空间的交集为 x，子空间上的垂足到原点的距离为$\frac{b_i}{||A_i||}$。

列空间：$\sum_{i}{a_ix_i}=b$，n 个列向量$a_i$的线性组合为 b。

### 齐次方程组 Homogeneous Systems

A system of linear equations of the form $Ax=0$ is called _homogeneous_.

A system of linear equations of the form $Ax=b$ for $b\ne0$ is called _inhomogeneous_.

A homogeneous system always has the solution $x=0$. This is called the _trivial solution_. Any nonzero solution is called _nontrivial_.

The equation $Ax=0$ has a nontrivial solution $\iff$ there is a free variable $\iff$ A has a column without a pivot position.

$Ax=0$ means x is orthogonal to every row of A, because its inner product is zero.
Every x in the null space of A is orthogonal to the row space of A.
Every y in the null space of Aᵀ is orthogonal to the column space of A.

The set of solutions to a homogeneous equation $Ax=0$ is a span. The number of free variables is called the _dimension_ of the solution set.

We can parametrize the solution sets using the free variables.

If $Ax=b$ is consistent, the set of solutions to is obtained by taking one _particular solution_ $p$ of $Ax=b$, and adding all solutions of $Ax=0$.
The solution set is a _translate of a span_.

If Ap=b and Ax=0, A(x+p)=Ax+Ap=0+b=b, then A(x+p)=b.

If Ap=b and Ax=b, A(x−p)=Ax−Ap=b−b=0, then A(x−p)=0.

**General = Particular + Homogeneous**

Any linear system’s solution set has the form

$$
\{\bm{p} + \bm{u} | \bm{u} ∈ Ker A\}
$$

i.e. any solution $x$ of $Ax=b$ can be expressed as the sum of the particular solution $\bm{p}$ and a solution $\bm{u}$ of the homogeneous system $Au=0$.

By setting exactly one free variable to 1 and the rest to 0, we can find the basis vector according to this free variable.
We can set all free variables to zero, the remaining pivot variables forming an inhomogeneous equation system with a unique solution.
Then create the particular solution by extend the unique solution with zero components of the free variables.

### 矩阵乘法

1. $(AB)_{ij}=A_i\cdot b_j$
2. $AB = [Ab_1\ ...\ Ab_n]$
3. $AB = \begin{bmatrix}A_1B\\...\\A_nB\end{bmatrix}$
4. $AB = \sum{a_iB_j}$

#### 线性无关 Linear Independence

A set of vectors $\{v_1,v_2,...,v_k\}$ is _linearly independent_ if the vector equation

$$
x_1v_1+x_2v_2+···+x_kv_k=0
$$

has only the trivial solution $x_1=x_2=···=x_k=0$. The set $\{v_1,v_2,...,v_k\}$ is _linearly dependent_ otherwise.

A wide matrix (a matrix with more columns than rows) has linearly dependent columns. Because $A$ cannot have a pivot in every column (it has at most one pivot per row), so its columns are automatically linearly dependent.

##### Facts about linear independence

1. Two vectors are linearly dependent if and only if they are collinear, i.e., one is a scalar multiple of the other.
2. Any set containing the zero vector is linearly dependent.
3. If a subset of $\{v_1,v_2,...,v_k\}$ is linearly dependent, then $\{v_1,v_2,...,v_k\}$ is linearly dependent as well.

##### Theorem

A set of vectors $\{v_1,v_2,...,v_k\}$ is linearly dependent if and only if one of the vectors is in the span of the other ones.

Any such vector may be removed without affecting the span.

##### Definition

A _subspace_ of $R^n$ is a subset V of $R^n$ satisfying:

1. **_Non-emptiness:_** The zero vector is in V.
2. **_Closure under addition:_** If u and v are in V, then u+v is also in V.
3. **_Closure under scalar multiplication:_** If v is in V and c is in R, then cv is also in V.

##### Theorem(Spans are Subspaces and Subspaces are Spans)

If $v_1,v_2,...,v_p$ are any vectors in $R^n$, then $Span\{v_1,v_2,...,v_p\}$ is a subspace of $R^n$. Moreover, any subspace of $R^n$ can be written as a span of a set of p linearly independent vectors in $R^n$ for p≤n.

##### Definition

Let A be an m×n matrix.

- The _column space_ of A is the subspace of $R^m$ spanned by the columns of A. It is written Col(A).

- The _null space_ of A is the subspace of $R^n$ consisting of all solutions of the homogeneous equation Ax=0:

$$
Nul(A)=\{x \in R^n | Ax=0\}.
$$

The null space of a matrix is the solution set of a homogeneous system of equations. To find a spanning set for the null space, one has to solve a system of homogeneous equations.

When asking questions about a subspace, it is usually best to rewrite the subspace as a column space or a null space.

The null space of a matrix is also called the kernel of matrix. Kernels play an important role in linear transformations.

##### Definition

Let V be a subspace of $R^n$. A _basis_ of V is a set of vectors $\{v_1,v_2,...,v_m\}$ in V such that:

1. $V=Span\{v_1,v_2,...,v_m\}$, and
2. the set $\{v_1,v_2,...,v_m\}$ is linearly independent.

The number of vectors in any basis of V is called the _dimension_ of V, and is written dimV.

##### Theorem

The pivot columns of a matrix A form a basis for Col(A).

A matrix and its reduced row echelon form generally have different column spaces.

Computing a basis for a span is the same as computing a basis for a column space.

##### Theorem

The vectors attached to the free variables in the parametric vector form of the solution set of Ax=0 form a basis of Nul(A).

##### Basis Theorem

Let V be a subspace of dimension m. Then:

- Any m linearly independent vectors in V form a basis for V.
- Any m vectors that span V form a basis for V.

##### Definition

Let $B=\{v_1,v_2,...,v_m\}$ be a basis of a subspace V, and let

$$
x=c_1v_1+c_2v_2+···+c_mv_m
$$

be a vector in V. The coefficients $c_1,c_2,...,c_m$ are the _coordinates of x with respect to B_.

Any vector x in V can be written as a linear combination

$$
x=c_1v_1+c_2v_2+···+c_mv_m
$$

in exactly one way.

##### Definition

The _rank_ of a matrix A, written rank(A), is the dimension of the column space Col(A).

The _nullity_ of a matrix A, written nullity(A), is the dimension of the null space Nul(A).

The rank of A is equal to the number of pivot columns, and the nullity of A is equal to the number of free variables.

##### Rank Theorem

If A is a matrix with n columns, then

$$
rank(A)+nullity(A)=n.
$$

In other words, for any consistent system of linear equations,

(dim of column span)+(dim of solution set)=(number of variables).

## Matrices as Functions

Let A be a $m×n$ matrix. Consider the matrix equation $b=Ax$, we think of A as a function with independent variable x and dependent variable b.

- The independent variable (the input) is x, which is a vector in $R^n$.
- The dependent variable (the output) is b, which is a vector in $R^m$.

##### Definition

The _identity transformation_ $Id_{R^n}:R^n→R^n$ is the transformation defined by the rule

$$
Id_{R^n}(x)=x\ for\ all\ x\ in\ R^n.
$$

##### Definition

Let A be an m×n matrix. The _matrix transformation_ associated to A is the transformation

$$
T:R^n→R^m\ defined\ by\ T(x)=Ax.
$$

The _range_ of T is the column space of A.

In the case of an n×n square matrix, the domain and codomain of T(x)=Ax are both $R^n$. In this situation, one can regard T as _operating on_ $R^n$: it moves the vectors around in the same space.

##### Definition(One-to-one transformations)

A transformation $T:R^n→R^m$ is _one-to-one_ if, for every vector b in $R^m$, the equation T(x)=b has _at most one_ solution x in $R^n$.

The following statements are equivalent:

1. T is one-to-one.
2. For every b in $R^m$, the equation T(x)=b has at most one solution.
3. For every b in $R^m$, the equation Ax=b has a unique solution or is inconsistent.
4. Ax=0 has _only_ the trivial solution.
5. The columns of A are linearly independent.
6. A has a pivot in every column.
7. The range of T has dimension n.

##### Definition(Onto transformations)

A transformation $T:Rn→Rm$ is _onto_ if, for every vector b in $R^m$, the equation $T(x)=b$ has _at least one_ solution $x$ in $R^n$.

Here are some equivalent ways of saying that T is onto:

- The range of T is equal to the codomain of T.
- Every vector in the codomain is the output of some input vector.

The following statements are equivalent:

1. T is onto.
2. T(x)=b has at least one solution for every b in $R^m$.
3. Ax=b is consistent for every b in $R^m$.
4. The columns of A span $R^m$.
5. A has a pivot in every row.
6. The range of T has dimension m.

##### Wide matrices do not have one-to-one transformations.

##### Tall matrices do not have onto transformations.

##### One-to-one is the same as onto for square matrices.

If a matrix transformation $T:R^m→R^n$ is both one-to-one and onto, then $m=n$.

##### Definition

A _linear transformation_ is a transformation $T:R^n→R^m$ satisfying

$$
T(u+v)=T(u)+T(v) \newline
T(cu)=cT(u)
$$

for all vectors u,v in $R^n$ and all scalars c.

Since a matrix transformation satisfies the two defining properties, it is a linear transformation.

##### Facts about linear transformations

Let $T:R^n→R^m$ be a linear transformation. Then:

1. T(0)=0.

2. For any vectors $v_1,v_2,...,v_k$ in $R^n$ and scalars $c_1,c_2,...,c_k$, we have

$$
T(c_1v_1+c_2v_2+···+c_kv_k)=c_1T(v_1)+c_2T(v_2)+···+c_kT(v_k).
$$

A linear transformation necessarily takes the zero vector to the zero vector. The second fact is called the _superposition principle_.

##### Standard coordinate vectors

The _standard coordinate vectors in $R^n$_ are the n vectors: $e_1,e_2,...,e_n$.

The $i$th entry of $e_i$ is equal to 1, and the other entries are zero.

Multiplying a matrix by $e_i$ simply selects its $i$th column.

##### Theorem(The matrix of a linear transformation)

Let $T:R^n→R^m$ be a linear transformation. Let A be the m×n matrix

$$
A=\begin{bmatrix}
   | & | & & |  \\
   T(e_1) & T(e_2) & ... & T(e_n) \\
   | & | & & |
\end{bmatrix}
$$

Then T is the matrix transformation associated with A: that is, $T(x)=Ax$.

The matrix A in the above theorem is called the _standard matrix_ for T. The columns of A are the vectors obtained by evaluating T on the n standard coordinate vectors in Rn.

The composition of matrix transformations corresponds to a notion of _multiplying_ two matrices together.

##### Definition(Matrix multiplication)

Let A be an m×n matrix and let B be an n×p matrix. Denote the columns of B by $v_1,v_2,...,v_p$:

$$
B=\begin{bmatrix}
   | & | & & |  \\
   v_1 & v_2 & ... & v_n \\
   | & | & & |
\end{bmatrix}
$$

The _product_ AB is the m×p matrix with columns $Av_1,Av_2,...,Av_p$:

$$
AB=\begin{bmatrix}
   | & | & & |  \\
   Av_1 & Av_2 & ... & Av_n \\
   | & | & & |
\end{bmatrix}.
$$

If A is a square matrix, then we can multiply it by itself; we define its _powers_ to be $A^2=AA, A^3=AAA$ etc.

- Matrix multiplication is not commutative.

- Matrix multiplication does not satisfy the cancellation law: $AB=AC$ does not imply $B=C$, even when $A\ne0$.

- It is possible for $AB=0$, even when $A\ne0$ and $B\ne0$.

##### Theorem

Let $T:R^n→R^m$ and $U:R^p→R^n$ be linear transformations, and let A and B be their standard matrices, respectively, so A is an m×n matrix and B is an n×p matrix. Then $T◦U:R^p→R^m$ is a linear transformation, and its standard matrix is the product $AB$.

The matrix of the composition of two linear transformations is the product of the matrices of the transformations. This is the one and only reason that matrix products are defined in this way.

Let $T,U:R^n→R^m$ be linear transformations with standard matrices A,B, respectively, and let c be a scalar.

- The standard matrix for T+U is A+B.
- The standard matrix for cT is cA.

##### Definition

Let A be an n×n (square) matrix. We say that A is _invertible_ if there is an n×n matrix B such that

$$
AB=I_n\ and\ BA=I_n.
$$

In this case, the matrix B is called the _inverse_ of A, and we write $B=A^{-1}$.

We restrict ourselves to _square_ matrices when we discuss matrix invertibility.

Let A and B be invertible n×n matrices.

1. $A^{-1}$ is invertible, and its inverse is $(A^{−1})^{−1}=A$.
2. $AB$ is invertible, and its inverse is $(AB)^{−1}=B^{−1}A^{−1}$.

##### Theorem

Let A be an n×n matrix, and let $(A|I_n)$ be the matrix obtained by augmenting A by the identity matrix. If the reduced row echelon form of $(A|I_n)$ has the form $(I_n|B)$, then A is invertible and $B=A^{−1}$. Otherwise, A is not invertible.

Row reducing $(A|I_n)$ is equivalent to solving the n systems of linear equations $Ax_1=e_1,Ax_2=e_2,...,Ax_n=e_n$, and $B=[x_1, x_2, ..., x_n]$.

##### Theorem

Let A be an invertible n×n matrix, and let b be a vector in $R^n$. Then the matrix equation $Ax=b$ has exactly one solution: $x=A^{−1}b$.

The advantage of solving a linear system using inverses is that it becomes much faster to solve the matrix equation Ax=b for other, or even unknown, values of b.

A linear transformation $T:R^n→R^n$ is invertible if and only if it is both one-to-one and onto.

##### Theorem

Let $T:R^n→R^n$ be a linear transformation with standard matrix A. Then T is invertible if and only if A is invertible, in which case $T^{-1}$ is linear with standard matrix $A^{−1}$.

##### Invertible Matrix Theorem

Let A be an n×n matrix, and let $T:R^n→R^n$ be the matrix transformation T(x)=Ax. The following statements are equivalent:

1. A is invertible.
2. A has n pivots.
3. Nul(A)={0}.
4. The columns of A are linearly independent.
5. The columns of A span $R^n$.
6. Ax=b has a unique solution for each b in $R^n$.
7. T is invertible.
8. T is one-to-one.
9. T is onto.

### 行列式 Determinant

The determinant of a square matrix A is a real number det(A).

##### Definition

The _determinant_ is a function

$$
det:\{squarematrices\}→R
$$

satisfying the following properties:

1. Doing a row replacement on A does not change det(A).
2. Scaling a row of A by a scalar c multiplies the determinant by c.
3. Swapping two rows of a matrix multiplies the determinant by −1.
4. The determinant of the identity matrix In is equal to 1.

This definition tells us how to compute the determinant: we do row reduce and keep track of the changes, then we compute the determinant in the opposite order.

No matter which row operations you do, you will always compute the same value for the determinant.

The computational complexity of row reduction is O(n3); it is an efficient way either by hand or by computer.

##### Definition

- The _diagonal_ entries of a matrix A are the entries $a_{11},a_{22},...$
- A square matrix is called _upper-triangular_ if its nonzero entries all lie above the diagonal, and it is called _lower-triangular_ if its nonzero entries all lie below the diagonal. It is called _diagonal_ if all of its nonzero entries lie on the diagonal, i.e., if it is both upper-triangular and lower-triangular.

##### Proposition

Let A be an n×n matrix.

1. If A has a zero row or column, then det(A)=0.
2. If A is upper-triangular or lower-triangular, then det(A) is the product of its diagonal entries.

##### Invertibility Property

A square matrix is invertible if and only if $det(A)\ne0$.

##### Multiplicativity Property

If A and B are n×n matrices, then $det(AB)=det(A)det(B)$.

If A is invertible, then we define$A^{−2}=A^{−1}A^{−1}, \ A^{−3}=A^{−1}A^{−1}A^{−1}$ etc.

For completeness, we set $A^0=I_n$ if $A\ne0$.

If A is a square matrix, then $det(A^n)=det(A)^n$ for all n≥1.

If A is invertible, then the equation holds for all n≤0 as well; in particular,

$det(A^{−1})=\frac{1}{det(A)}$.

##### Definition

The _transpose_ of an m×n matrix A is the n×m matrix $A^T$ whose rows are the columns of A. In other words, the ij entry of $A^T$ is $a_{ji}$.

Let A be an m×n matrix, and let B be an n×p matrix. Then $(AB)^T=B^TA^T$.

##### Transpose Property

For any square matrix A, we have $det(A)=det(A^T)$.

##### Definition

The _paralellepiped_ determined by n vectors $v_1,v_2,...,v_n$ in $R^n$ is the subset

$$
P=\{a_1v_1+a_2v_2+···+a_nv_n | 0≤a_1,a_2,...,a_n≤1\}.
$$

In other words, a parallelepiped is the set of all linear combinations of n vectors with coefficients in [0,1].

##### Theorem(Determinants and volumes)

Let $v_1,v_2,...,v_n$ be vectors in $R^n$, let P be the parallelepiped determined by these vectors, and let A be the matrix with rows $v_1,v_2,...,v_n$. Then the absolute value of the determinant of A is the volume of P:

$$
|det(A)|=vol(P).
$$

We can think of the determinant as a _signed_ volume.

##### Theorem

Let A be an n×n matrix, and let $T:R^n→R^n$ be the associated matrix transformation T(x)=Ax. If S is any region in $R^n$, then

$$
vol(T(S))=|det(A)|·vol(S).
$$

## 本征值和本征向量 Eigenvalues and Eigenvectors

Linear equations Ax=b come from steady state problems.
Eigenvalues have their greatest importance in dynamic problems.

##### Definition

Let A be an n×n matrix.

1. An _eigenvector_ of A is a _nonzero_ vector v in $R^n$ such that $Av=λv$, for some scalar λ.
2. An _eigenvalue_ of A is a scalar λ such that the equation $Av=λv$ has a _nontrivial_ solution.

If $Av=λv$ for $v\ne0$, we say that $λ$ is the _eigenvalue for_ $v$, and that $v$ is an _eigenvector for_ $λ$.

The German prefix “eigen” roughly translates to “self” or “own”. On the other hand, “eigen” is often translated as “characteristic”; we may think of an eigenvector as describing an intrinsic, or characteristic, property of A.

##### Note

Eigenvalues and eigenvectors are only for square matrices. Eigenvectors are _by definition nonzero_. Eigenvalues may be equal to zero.

$Av=λv$ means that $Av$ and $λv$ are _collinear with the origin_, so $Av$ and $v$ lie on the same line through the origin.

$Ax=0$ is a special case of $λ=0$.
$Av=λv \implies A^nv=λ^nv$
$Av_i=λ_iv_i \implies A(c_1v_1+c_2v_2)=c_1λ_1v_1+c_2λ_2v_2$
$\implies A^n(c_1v_1+c_2v_2)=c_1λ_1^nv_1+c_2λ_2^nv_2$

If $λ_i \lt 1$, $λ_i^N \approx 0$ for big N, $v_i$ is a decaying mode.
If $λ_i = 1$, corresponding eigenvector $v_i$ is a steady state.

**Lemma** An eigenvector has at most one eigenvalue.
Proof: Assume $A·v=λ_1v$ and $A·v=λ_2v$. Then: $0 =A·v−A·v=λ_1v−λ_2v= (λ_1−λ_2)v$.
Since $v\ne0$, we must have $λ_1−λ_2=0$, and thus $λ_1=λ_2$.

**Lemma** If $v$ is an eigenvector, then $cv$ is also an eigenvector, for each $c\ne0$.
Proof: $A(cv)=cAv=c(λv)=λ(cv)$.

**Lemma** If an eigenvalue λ occurs n times, then there are at most n independent eigenvectors for this λ.

Linear combinations of eigenvectors with the same eigenvalue λ are also eigenvectors with eigenvalue λ,
they form a subspace of dimension n: the eigenspace of λ.

The eigenvectors of A with eigenvalue λ are the nontrivial solutions of the matrix equation $(A−λI_n)v=0$, i.e., the nonzero vectors in $Nul(A−λI_n)$, it is called the _λ-eigenspace_ of A.

**Theorem.** Eigenvectors with distinct eigenvalues are linearly independent.

**Collary.** An n×n matrix A has at most n eigenvalues.

If thenn×n matrix A is symmetric then eigenvectors corresponding to different eigenvalues must be orthogonal to each other.
Furthermore, in this case there will exist n linearly independent eigenvectors for A, it's always possible to find some set of n eigenvectors which are mutually orthogonal.

##### Fact

Let A be an n×n matrix.

1. The number 0 is an eigenvalue of A if and only if A is not invertible.
2. In this case, the 0-eigenspace of A is Nul(A).

##### Invertible Matrix Theorem

Let A be an n×n matrix, and let $T:R^n→R^n$ be the matrix transformation $T(x)=Ax$. The following statements are equivalent:

1. A is invertible.
2. A has n pivots.
3. Nul(A)={0}.
4. The columns of A are linearly independent.
5. The columns of A span $R^n$.
6. Ax=b has a unique solution for each b in $R^n$.
7. T is invertible.
8. T is one-to-one.
9. T is onto.
10. $det(A)\ne0$.
11. 0 is not an eigenvalue of A.

##### Definition

Let A be an n×n matrix. The _characteristic polynomial_ of A is the function f(λ) given by $f(λ)=det(A−λI_n)$.

##### Theorem(Eigenvalues are roots of the characteristic polynomial)

Let A be an n×n matrix, and let $f(λ)=det(A−λI_n)$ be its characteristic polynomial. Then a number $λ_0$ is an eigenvalue of A if and only if $f(λ_0)=0$.

##### Corollary

If A is an upper- or lower-triangular matrix, then the eigenvalues of A are its diagonal entries.

##### Definition

The _trace_ of a square matrix A is the number Tr(A) obtained by summing the diagonal entries of A: $Tr(A)=\sum_{i}a_{ii}$.

##### Theorem

Let A be an n×n matrix, and let $f(λ)=det(A−λI_n)$ be its characteristic polynomial. Then f(λ) is a polynomial of degree n. Moreover, f(λ) has the form

$$
f(λ)=(−1)^nλ^n+(−1)^{n−1}Tr(A)λ^{n−1}+···+det(A).
$$

Since a polynomial of degree n has at most n roots, this gives another proof of the fact that an n×n matrix has at least one and at most n distinct eigenvalues.

It is known that there is [no algebraic formula](https://en.wikipedia.org/wiki/Abel%E2%80%93Ruffini_theorem) for the roots of a general polynomial of degree at least 5. In practice, the roots of the characteristic polynomial are found [numerically by computer](https://en.wikipedia.org/wiki/Newton%27s_method).

##### Theorem

The sum of the eigenvalues of a matrix equals its trace.
The product of the eigenvalues equals its determinant.
For repeated eigenvalues, one must add or multiply them according to their multiplicity.

### 相似矩阵 Similar Matrices

##### Definition

Two n×n matrices A and B are _similar_ if there exists an invertible n×n matrix C such that $A=CBC^{−1}$.

Similarity is an _equivalence relation_. Similar matrices do the same thing in different coordinate systems.

##### Fact

Similar matrices have the same characteristic polynomial.

Similar matrices have the same eigenvalues.

Similar matrices also have the same trace and determinant.

Suppose that $A=CBC^{−1}$. Then

$v$ is an eigen vector of A ⇒ $C^{−1}v$ is an eigen vector of B;

$v$ is an eigen vector of B ⇒ $Cv$ is an eigen vector of A.

本征值不变，本征向量做线性映射。

Diagonal matrices are the easiest kind of matrices to understand: they just scale the coordinate directions by their diagonal entries. Therefore, if a matrix is similar to a diagonal matrix, it is also relatively easy to understand.

##### Definition

An n×n matrix A is _diagonalizable_ if it is similar to a diagonal matrix.

##### Diagonalization Theorem

An n×n matrix A is diagonalizable if and only if A has n linearly independent eigenvectors $v_i$.

In this case, $A=CDC^{−1}$, $Ce_i=v_i$,

$De_i=C^{−1}ACe_i=C^{−1}Av_i=C^{−1}λ_iv_i=λ_iC^{−1}v_i=λ_ie_i$.

There are generally many different ways to diagonalize a matrix, corresponding to different orderings of the eigenvalues of that matrix.

If matrix A has k distinct eigenvalues, then the corresponding eigenvectors $v_1,...,v_k$ are linearly independent.

The eigenvalues of a symmetric matrix are real, the eigenvectors always form an orthogonal basis of the underlying Euclidean space.

##### Recipe: Diagonalization

Let A be an n×n matrix. To diagonalize A:

1. Find the eigenvalues of A using the characteristic polynomial.
2. For each eigenvalue λ of A, compute a basis $B_λ$ for the λ-eigenspace.
3. If there are fewer than n total vectors in all of the eigenspace bases $B_λ$, then the matrix is not diagonalizable.
4. Otherwise, the n vectors $v_1,v_2,...,v_n$ in the eigenspace bases are linearly independent, and $A=CDC^{−1}$.

##### Diagonalizability has nothing to do with invertibility.

A matrix is real diagonalizable if and only if its eigenspace has the same dimension as its multiplicity. and has all real eigenvalues.

##### Definition

Let A be an n×n matrix, and let λ be an eigenvalue of A.

1. The _algebraic multiplicity_ of λ is its multiplicity as a root of the characteristic polynomial of A.

2. The _geometric multiplicity_ of λ is the dimension of the λ-eigenspace.

- If A has an eigenvalue λ with algebraic multiplicity 1, then the λ-eigenspace is a _line._

- 1≤(the geometric multiplicity of λ)≤(the algebraic multiplicity of λ).

Let A be an n×n matrix. The following are equivalent:

1. A is diagonalizable.
2. The sum of the geometric multiplicities of the eigenvalues of A is equal to n.
3. The sum of the algebraic multiplicities of the eigenvalues of A is equal to n, and for each eigenvalue, the geometric multiplicity equals the algebraic multiplicity.

_Diagonalizable_ matrices are similar if and only if they have the same characteristic polynomial, or equivalently, the same eigenvalues with the same algebraic multiplicities.

### Orthogonal Matrix

A matrix $Q$ is orthogonal if and only if $Q^⊤Q = I$, which states that the columns (and rows as well) of Q are mutually orthogonal unit vectors.

Every orthogonal matrix is either a rotation matrix or the product of a rotation matrix and a reflection matrix.

Length is preserved: $ ||Qx||^2 = xᵀQᵀQx = xᵀx = ||x||^2 $

Eigenvalues: $ ||Qx||^2 = |λ|^2||x||^2 \implies |λ|^2=1 $

### Permutation Matrix

A permutation matrix is a square matrix obtained from the same size identity matrix by a permutation of rows. Such a matrix is always row equivalent to an identity.

Every row and every column of a permutation matrix contain exactly one nonzero entry, which is 1. There are n! permutation matrices of size n.

Every permutation matrix is a product of elementary row-interchange matrices. Every elementary permutation matrix is symmetric, $P^T=P$. Since interchanging two rows is a self-reverse operation, every elementary permutation matrix is invertible and agrees with its inverse $P^{-1}=P$.

A product of permutation matrices is again a permutation matrix. The inverse of a permutation matrix is again a permutation matrix. In fact, $P^{-1}=P^T$.

Left multiplication by a permutation matrix rearranges the corresponding rows.
Right multiplication by a permutation matrix rearranges the corresponding columns.
Some power of a permutation matrix is the identity.

### Matrices with Complex Eigenvalues

As a consequence of the [fundamental theorem of algebra](https://textbooks.math.gatech.edu/ila/complex-eigenvalues.html "Fundamental Theorem of Algebra A.0.30") as applied to the characteristic polynomial, we see that: Every n×n matrix has exactly n complex eigenvalues, counted with multiplicity.

Let A be a matrix with real entries. If $λ$ is a complex eigenvalue with eigen vector $v$, then $\overline{λ}$ is a complex eigenvalue with eigenvector $\overline{v}$. In other words, both eigenvalues and eigenvectors come in conjugate pairs.

##### Definition

A _rotation-scaling matrix_ is a 2×2 matrix of the form

$$
A=\begin{bmatrix}
   a & -b  \\
   b & a
\end{bmatrix},
$$

where a and b are real numbers, not both equal to zero. The eigenvalues of A are $λ=a±bi$.

##### Rotation-Scaling Theorem

Let A be a 2×2 real matrix with a complex (non-real) eigenvalue λ, and let v be an eigenvector. Then $A=CBC^{−1}$ for

$$
C=\begin{bmatrix}
   | & |  \\
   Re(v) & Im(v) \\
   | & |
\end{bmatrix},\ and\ B=\begin{bmatrix}
   Re(λ) & Im(λ)  \\
   −Im(λ) & Re(λ)
\end{bmatrix}.
$$

In particular, A is similar to a rotation-scaling matrix that scales by a factor of $|λ|=\sqrt{det(B)}$.

##### Block Diagonalization of a 3×3 Matrix with a Complex Eigenvalue

Let $v_1$ be a (complex) eigenvector with eigenvalue $λ_1$, and let $v_2$ be a (real) eigenvector with eigenvalue $λ_2$. Then $A=CBC^{−1}$ for

$$
C=\begin{bmatrix}
   | & | & | \\
   Re(v) & Im(v) & v_2 \\
   | & | & |
\end{bmatrix},\ and\ B=\begin{bmatrix}
   Re(λ) & Im(λ) & 0 \\
   −Im(λ) & Re(λ) & 0 \\
   0 & 0 & λ_2
\end{bmatrix}.
$$

##### Definition

The _row space_ of a matrix A is the span of the rows of A, and is denoted Row(A).

##### Theorem

Let A be a matrix. Then the row rank of A is equal to the column rank of A.

### LU Decomposition

To solve Ax=b, find two matrices, L and U, where L is lower-triangular and U is upper-triangular, and A=LU. Then x is calculated in two steps: Ly=b and Ux=y.

### QR Decomposition

Decomposition of a matrix A into a product A = QR of an orthogonal matrix Q and an upper triangular matrix R.

Q can be abtained by applying the Gram-Schmidt process with normalization to these column vectors of A.

Every invertible matrix has an QR decomposition.

$QRx=b \implies x=R^{-1}Q^Tb$

pseudo-inverse of a matrix A is:

$$
\begin{gathered}
A^{†} = (A^T A)^{−1}A^T = ((QR))^T (QR))^{−1}(QR)^T= (R^TR)^{−1}(QR)^T=R^{-1}Q^T\\
A^{†}A = I
\end{gathered}
$$

### Eigenvalue Decomposition (EVD)

Let A be a square n × n matrix with n linearly independent eigenvectors $q_i$ (where i = 1, ..., n). Then A can be factorized as

$$
\mathbf{A}=\mathbf{Q}\mathbf{\Lambda}\mathbf{Q}^{-1}
$$

where Q is the square n × n matrix whose ith column is the eigenvector $x_i$ of A, and Λ is the diagonal matrix whose diagonal elements are the corresponding eigenvalues, $Λ_{ii} = λ_i$. Note that only diagonalizable matrices can be factorized in this way.

Diagonalizing a matrix is the same process as finding its eigenvalues and eigenvectors.

$$
A^n=QΛ^nQ^{-1}
$$

### Singular Value Decomposition (SVD)

Any real mxn matrix A can be decomposed uniquely as $A=UΣV^T$.

U is mxn and orthogonal (its columns are eigenvectors of $AA^T$).
V is nxn and orthogonal (its columns are eigenvectors of $A^TA$).
Σ is nxn diagonal (non-negative real values called singular values).
The number of non-zero singular values equals to the rank of matrix.
Order singular values as σ₁≥σ₂≥⋯≥σᵣ>0.

If A is a nxn nonsingular matrix, then its inverse is given by $A=UΣV^T \implies A^{−1}=VΣ^{−1}U^T$.

$Ax=UΣV^Tx$, applies rotation, stretch and rotation to a vector.

$AᵀA=VΣ^2Vᵀ$
$AAᵀ=UΣ^2Uᵀ$

$AV=UΣ \implies u_i=\frac{Av_i}{σ_i}$

$rank(A)=r, [u_{r+1}... u_m]$ is null space of Aᵀ, $[v_{r+r}...v_n]$ is null space of A.

$Av_i=σ_iu_i$, 如果 detA≠0, 取最小的$σ_i$对应的$v_i$可作为$Ax=0$的近似解。$v_i$也是 AᵀA 的最小本征值对应的本征向量。

$Ax=b$的近似解$x=A^{−1}b≈VΣ_0^{−1}U^Tb$，
其中$Σ_0^{−1}=\begin{cases}1/σ_i&\text{if }σ_i>t \\ 0&\text{otherwise}\end{cases}$，
计算精度高于$(A^TA)^{−1}A^Tb$。

If r < m or r < n, define pseudoinverse A⁺=VΣ⁺Uᵀ.

$$
‖Ax‖=‖UΣV^Tx‖=‖ΣV^Tx‖≤σ₁‖V^Tx‖=σ₁‖x‖
$$

The maximum value of $\dfrac{‖Ax‖}{‖x‖}$ equals σ₁.
The ratio $\dfrac{σ_{max}}{σ_{min}}$ governs the roundoff error in solving Ax=b.
Matlab warns you if the "condition number" is large, then x is unreliable.

### Least Squares

Let $A$ be an m×n matrix and let $b$ be a vector in $R^m$.
Solve $Ax=b$ by find a vector $\hat{x}$ that minimizes the least squares error ‖b-Ax‖.
Choose $A\hat{x}$ to be the projection of b in column space of A.
Then $b-A\hat{x}$ is in the null space of Aᵀ.
So $ A^T(b-A\hat{x})=0 \implies A^TA\hat{x}=A^Tb$.

There may be more than one least squares solutions, but each has the same error $b-A\hat{x}$.

If $A^TA$ is invertible, the least-squares solution is $\hat{x}=(A^TA)^{−1}A^Tb$, and is a unique solution.

$A^TA$ is invertible, if and only if A has independent columns.

To compute the least-squares solution numerically, use QR decomposition instead.

$
\hat{x}=(A^TA)^{−1}A^Tb=((QR)^T(QR))^{−1}(QR)^Tb=(R^TR)^{−1}(QR)^Tb=R^{−1}Q^Tb
$

Fit points by least squares solution of yᵢ=axᵢ+b, fits a best line by minimizing the vertical distances.

#### Perpendicular Least Squares

Least squares estimator may fail when the number of explanatory variable is relatively large in comparison to the sample or if the variables are almost collinear.

Principal component analysis(PCA): the largest eigen value is the principal component.
PCA minimizes the error orthogonal (perpendicular) to the model line.

Covariance matrix $S=\dfrac{AᵀA}{m-1}$, m is the number of samples.

Total variance = σ₁²+⋯+σₙ² = λ₁+⋯+λₙ.

### Polar Decomposition

$A=UΣVᵀ=(UVᵀ)(VΣVᵀ)=QS$
Q is orthogonal and S is symmetric positive define.
$Q=UVᵀ$ is the nearest orthogonal matrix to A.
$S²=VΣ²Vᵀ=VΣUᵀUΣVᵀ=AᵀA$

### Difference between SVD and eigendecomposition

Consider the eigendecomposition $𝐴=𝑃𝐷𝑃^{−1}$ and SVD $𝐴=𝑈Σ𝑉^∗$. Some key differences are as follows,

- The vectors in the eigendecomposition matrix 𝑃 are not necessarily orthogonal, so the change of basis isn't a simple rotation. On the other hand, the vectors in the matrices 𝑈 and 𝑉 in the SVD are orthonormal, so they do represent rotations (and possibly flips).
- In the SVD, the nondiagonal matrices 𝑈 and 𝑉 are not necessairily the inverse of one another. They are usually not related to each other at all. In the eigendecomposition the nondiagonal matrices $𝑃$ and $𝑃^{−1}$ are inverses of each other.
- In the SVD the entries in the diagonal matrix Σ are all real and nonnegative. In the eigendecomposition, the entries of 𝐷 can be any complex number — negative, positive, imaginary, whatever.
- The SVD always exists for any sort of rectangular or square matrix, whereas the eigendecomposition can only exists for square matrices, and even among square matrices sometimes it doesn't exist.

### 广义本征向量 Generalized eigenvectors

A nonzero vector w satisfies $(A-λI)^kw=0$ for some $k>0$ and $λ\in\Complex$ is called a generailized eigenvector of the matrix A. $k=1$ is the standard eigenvector problem.

### 多项式本征值问题 Polynomial eigenvalue problem

- Linear eigenproblem, also called Generalized Eigenvalue Problem in some literature. $B=I$ is the standard eigenvector problem.

$$
Av=λBv \implies (A-λB)v=0
$$

- Quadratic eigenvalue problem

$$
(λ^2A_2+λA_1+A_0)v=0
$$

- Polynomial eigenvalue problem

$$
(\sum_{i}{λ^iA_i})v=0
$$

## Adequacy of Solutions

A system of equations is considered to be well-conditioned if a small change in the coefficient matrix or a small change in the right hand side results in a small change in the solution vector.

A system of equations is considered to be ill-conditioned if a small change in the coefficient matrix or a small change in the right hand side results in a large change in the solution vector.

If a system of equations is ill-conditioned, we cannot trust the solution as much.

For a m×n matrix, the row sum norm of A is defined as the maximum of the sum of the absolute value of the elements of each row.

$$
\|A\|_{\infty}=\max_{1\le i \le m}\sum_{j=1}^{n}|a_{ij}|
$$

For equation $AX=C$, $ \dfrac{\|ΔX\|}{\|X+ΔX\|} \le \|A\|\|A^{-1}\| \dfrac{\|ΔA\|}{\|A\|} $.

Define $Cond(A)=\|A\|\|A^{-1}\|$, the relative error in a solution vector norm is ≤ Cond (A) × relative error in right hand side vector norm.

## 实对称矩阵

实对称矩阵 A 的特征值都是实数，特征向量都是实向量。实对称矩阵 A 的不同特征值对应的特征向量是正交的，取 Q 为特征向量的单位向量组成的正交矩阵。

$$
\begin{gathered}
Sᵀ=S, Sx = λx, Sy = αy, λ≠α \\
λxᵀy = xᵀSᵀy = xᵀSy = αxᵀy \\
xᵀy = 0
\end{gathered}
$$

$$
SQ = QΛ \implies S=QΛQᵀ=\sum_{i}{λ_iq_iq_i^T}
$$

$$
Ax=b \implies QΛQ^Tx=b \implies Q^Tx=Λ^{-1}Q^Tb
$$

$$
q_i^Tx=λ_i^{-1}q_i^Tb \implies x=\sum_{i}{(λ_i^{-1}q_i^Tb)q_i}
$$

### 正定矩阵 (positive definite matrix)

一个 n 阶的实对称矩阵 A 是正定的，当且仅当对于任意的非零实系数向量 x，都有$xᵀAx > 0$。

正定矩阵的特征值都是正实数；对于任意的实矩阵 B，BᵀB 是正定的。

半正定矩阵是正定矩阵的推广。实对称矩阵 A 称为半正定的，如果二次型 xᵀAx 半正定，即对于任意不为 0 的实列向量 x，都有$xᵀAx \ge 0$.

### 二元一次方程组

$$
\begin{cases}
   ax+by=e \\
   cx+dy=f
\end{cases}
$$

$$
\begin{bmatrix}
   a & b \\
   c & d \\
\end{bmatrix}
\begin{bmatrix}
   x \\ y
\end{bmatrix}=\begin{bmatrix}
   e \\ f
\end{bmatrix}
$$

当$ad-bc≠0$时,

$$
\begin{cases}
x = \dfrac{de-bf}{ad-bc} \\\\
y = \dfrac{af-ce}{ad-bc}
\end{cases}
$$

$
A=\begin{bmatrix}
   a & b \\
   c & d \\
\end{bmatrix}\\
det(A)= ad-bc\\
tr(A)=a+d \\
λ^2-tr(A)λ+det(A)=0 \\
λ_1 = \cfrac{1}{2} ( a + d + \sqrt{(a-d)^2 + 4 b c}) \\
λ_2 = \cfrac{1}{2} ( a + d - \sqrt{(a-d)^2 + 4 b c}) \\
v_1 = (-\cfrac{-a + d - \sqrt{(a-d)^2 + 4 b c}}{2 c}, 1) = (a-λ_2, c) \\
v_2 = (-\cfrac{-a + d + \sqrt{(a-d)^2 + 4 b c}}{2 c}, 1) = (a-λ_1, c) \\
$

## 矢量叉乘

$A×B=(a,b,e)×(c,d,f)=(bf-de,ce-af,ad-bc)$

## 复数矩阵

Inner product: $zᴴz = \bar{z}ᵀz = ‖z‖²$
Conjugate transpose: Aᴴ = Āᵀ
Hermitian matrix: S=Sᴴ
Unitary matrix: Uᴴ=U⁻¹, UᴴU=I

## 数值计算

求 Ax=0 用 EVD，如果 A 不是方阵或不是对称矩阵，改为 AᵀAx=0。

求 Ax=b 用 SVD，如果 A 低阶可逆，可用 x=A⁻¹b。

```rust
/// rotate vector by perpendicular axis
fn rotate_vector(axis: &Vec3, vector: &Vec3, angle: f64) -> Vec3 {
    let (sin, cos) = angle.sin_cos();
    vector * cos + axis.cross(&vector) * sin
}

fn rotation_angle(a: Vec3, b: Vec3, n: Vec3) -> f64 {
    let ba = b - a;
    let na = n.cross(&a);
    let nna = n.cross(&na);
    (na.dot(&ba)).atan2(na.norm_squared() - nna.dot(&ba))
}

fn included_angle(a: Vec3, b: Vec3, n: Vec3) -> f64 {
    let pa = a - n * a.dot(&n);
    let pb = b - n * b.dot(&n);
    pa.angle(&pb)
}

fn point_on_normal_bisector(a: Point2, b: Point2, ratio: f64) -> Point2 {
    let center = (a + b) / 2.0;
    let perp_dir = (b - a).perp(); // returns (-y, x)
    center + perp_dir * ratio
}

fn skew_symmetric(v: Vector3<f64>) -> Matrix3<f64> {
    let mut ss = Matrix3::zeros();
    ss[(0, 1)] = -v[2];
    ss[(0, 2)] = v[1];
    ss[(1, 0)] = v[2];
    ss[(1, 2)] = -v[0];
    ss[(2, 0)] = -v[1];
    ss[(2, 1)] = v[0];
    ss
}
```
