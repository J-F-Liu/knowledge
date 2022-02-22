认识论的实在论，是说科学理论是对于世界的一个真实有效的描述。
但科学理论在不断地发展更新，所以对于世界的描述是趋近于精确的。

本体论的实在论，是说科学理论所构建的那些理论实体是实际存在的。
但微观粒子、电磁场、波函数等是无法直接观察的，我们只能观测现象，同样的现象可以有不同的理论解释。

结构实在论，或者叫关系实在论，是说数学方程是一种结构化的关系性的存在。
但数学形式或者数学结构这个理念的世界与物理现象的世界之间有个巨大的鸿沟。

物理结构实在论，是说数学方程是对物理结构的描述，真实的物理世界是结构化的。

质量是能量的量度：E=mc²，物质的质量不是组成它的粒子的质量之和。
具有能量，是物质存在的根本特征。

量子场论认为场更加基本，粒子只是场的激发态。
场是有能量的，一切物理现象都是场与场之间的相互作用。

人的行为，和组成人的基本粒子的物理学，是不同层面的问题。
量子力学能解释基本粒子的行为，但就算你完全掌握量子力学的计算方法，也解释不了一个单细胞生物是怎么运作的。这是因为从基本粒子到单细胞生物中间隔着很多层，一个单细胞生物是由无数个基本粒子组成的，你不可能一个粒子一个粒子地计算，那个运算量是不可接受的。你甚至连 10 个基本粒子的互动都算不过来，因为太复杂了。
你只能暂时忘记基本粒子，重新总结一些更宏观的规律。
逻辑门都是由晶体管组成的，CPU（中央处理器）是由逻辑门组成的，程序是 CPU 的操作，人工智能是程序实现算法——但是理解晶体管，可不一定就理解人工智能。每跨越一个层级，就是完全不同的原理。
这个现象也叫“涌现”——东西多了，它们就会表现出某种更宏观的、更高层面的逻辑。
所以就算有朝一日我们找到了物理学的统一理论，也不能说这个世界上就没有新的学问可以研究了，不同层面有不同层面的学问。

### 对称性与守恒量

诺特定理：系统的任何一个连续对称性都能对应一种守恒量。对称性可以简单地理解为 “不变性”。

对称性和守恒定律取决于相互作用的性质。弱相互作用会影响所有费米子，即所有自旋为半奇数的粒子。

时空对称性：

- 时间平移对称性 → 能量守恒
- 空间平移对称性 → 动量守恒
- 空间旋转对称性 → 角动量守恒
- 空间镜像对称性 → 宇称守恒 （弱相互作用下不守恒）

内禀对称性：

- 与电磁场耦合的全局 U(1)规范对称性 → 电荷守恒
- SU(3)对称性 → 色荷守恒

CPT 守恒：电荷(Charge)+宇称(Parity)+时间(Time) 守恒

洛伦兹对称性 → 光速守恒

规范对称性(gauge symmetry)在现代物理理论中非常重要。虽然我们把它叫做"对称性"，但比较现代的观点是把它看成一种"冗余"，它告诉我们描述不同物理的是一族数学上的等价类。
规范对称性的守恒荷等于 0，如果规范对称性带有可观测的荷，那么规范对称性就不再是一种冗余，而是代表了实际物理。

Gauge Freedom 规范自由度
The coordinate frame is specified and held fixed with respect to the chosen reference elements.
The freedom in the choice of coordinate fixing rules is called gauge freedom.

Coordinates are a very convenient device for reducing geometry to algebra, but they come at the price of some arbitrariness.
The coordinate system can be changed at any time, without affecting the underlying geometry.
This is very familiar, but it leaves us with two problems:
(i) algorithmically, we need some concrete way of deciding which particular
coordinate system to use at each moment, and hence breaking the arbitrariness;
(ii) we need to allow for the fact that the results may look quite different under different choices,
even though they represent the same underlying geometry.

Different gauges represent different but geometrically equivalent coordinatization rules.
Coordinate system independent quantities are called gauge invariants.
It is only for gauge invariants that we can find meaningful values and covariances.

Given the wide range of gauges and the significant impact that they have on the appearance of the state updates and covariance matrix,
it is useful to ask which gauges give the “smallest” or “best behaved” updates and covariances.
