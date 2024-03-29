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
- 引力场对应 SO(3, 1)

CPT 守恒：电荷(Charge)+宇称(Parity)+时间(Time) 守恒

洛伦兹对称性 → 光速守恒

谈论对称性时，我们需要注意区分全局对称性（global symmetry）和局域对称性（local symmetry）。前者是整个流形总体所拥有的对称性，而后者则是每个点各自具备的属性。
局域对称性在物理中的重要地位要远大于全局对称性，具有局域对称性的场统称为规范场（gauge field）。

描述对称性的数学语言是群，每一种对称性都对应特定的群。O(n)群和 SO(n)群对应着 n 维实数空间中的旋转对称，而 U(n)群和 SU(n)群则代表 n 维复数空间中的旋转对称。

规范对称性(gauge symmetry)在现代物理理论中非常重要。虽然我们把它叫做"对称性"，但比较现代的观点是把它看成一种"冗余"，它告诉我们描述不同物理的是一族数学上的等价类。
规范对称性的守恒荷等于 0，如果规范对称性带有可观测的荷，那么规范对称性就不再是一种冗余，而是代表了实际物理。

之所以我们称它为“规范”对称性，因为它是我们用来测量，或者说“规范”各种量值的单位的对称性。

利用规范对称性来描述电磁相互作用和弱相互作用，需要分别用到圆对称性和球对称性。

在时空的每一点上，都有一个圆周旋转的对称性。可以简单想象时空中的每一点都有一个额外的圆，这是一个额外的维度。
在物理学中，我们不知道这个圆是否是真实存在的，也不知道是否真的有一个额外的维度。
我们所知道的是，物理上要求的对称性与额外维度导致的对称性是相似的。
在物理学中，我们喜欢做尽可能少的假设，额外的维度不是一个必要的假设，只有对称性才是。

当一个电子在真空中运动时，它会连续地从一个时空点移动到下一个时空点。
规范理论中的计算通常会先假设这些时空点是离散的，然后在所有时空点彼此非常接近时，将它们看作一个连续体，这就是“连续性极限”。

弱力也同样可以用规范理论来理解。这里每一个时空点上都有一个球的旋转对称性，这些弱球的总体被称为希格斯场。
利用弱球进行重新定向需要三个量，需要确定一个旋转轴（两个量）和一个围绕旋转轴旋转的角度（第三个量），类似于欧拉角。
此时，这三个量会分别对应三种磁场，而不再像电磁力一样仅仅只有一种磁场。

对于一个给定强度的波来说，激发这个波所需的能量会依赖其波长，随着波长越来越长，其能量消耗会越来减小，而当波长非常非常长的时候，激发所需能量便于这个波对应粒子的质量直接相关。

一个典型的衰变过程是一个原子核外的自由中子会花大约 15 分钟的时间，衰变成一个质子、一个电子和一个（反电子）中微子。
电磁相互作用的对称性对应于一个在圆上和球上的组合旋转，SU(2)×U(1)群。因此，做“电磁规范变换”会产生一个弱球上的旋转，这可以使得 W± 玻色子变成带电粒子。
带有不同电荷的电子和中微子其实是同一种粒子，只不过它们在弱球上的旋转方式不同。
在弱球上不同的旋转方式就对应着不同的电荷。如上所述，这个把电磁力和弱力统一在一起的理论被称为电弱统一理论。

杨振宁和米尔斯发现杨-米尔斯理论最初是为了描述介子，然而现在却用它来描述弱相互作用和强相互作用。
一个好的想法可能对它原始的目标不是很奏效，却可能对别的问题很有用，杨-米尔斯理论就是一个很好的例子。
描述规范场的数学这个理论提出之前就已经被数学家发现了，他们把这些结构称为纤维丛。

无论是否引入希格斯场，我们都可以为光子以外的其它构成物质的粒子（比如电子）加上质量的属性。
之所以我们需要让希格斯来完成这一使命（赋予电子质量），原因和弱相互作用具有的一种奇异的性质有关。
比如电子具有“自旋”这个事实，

光有两种偏振状态，带有左旋和右旋两种偏振的电磁波，沿着传播方向具有自旋角动量。
描述光时称偏振，描述其他粒子时称极化。电子和中微子像光一样具有极化性质，这来源于它们也有自旋角动量，

当这些粒子移动的时候，可以根据它们移动的方向，来定义它们的自旋角动量是“左手的”还是“右手的”。
想象一个向上运动的右手有质量粒子，在以快于它的速度向上移动的参考系里，这个粒子就变成了向下运动，而此时自旋角动量方向保持不变，于是在这个参考系里它就变成了一个左手的粒子。
而一个没有质量的粒子无法处于静止不动状态，它永远在以光速运动着，并且观察者也不可能以比它还快的速度运动来反转它的运动方向。

弱相互作用的奇异性质：弱相互作用对于左手和右手粒子来说是不同的，只有左手粒子会参与弱相互作用。这是一个非常令人意外的性质，因为它表明弱相互作用破坏了反射对称性。
在“弱球”上，左手电子和右手中微子基本上就是同一种粒子，只是它们的运动方向不同。这意味着在弱相互作用下，左手电子和右手中微子可以相互转化。而右手电子则感受不到弱相互作用，我们不知道相应的左手中微子是否存在，实际上它也不必真的存在。并且，这两种左右手粒子截然不同的差别只在它们都以光速运动的时候才可能出现。
然而，电子是有质量的粒子，和希格斯场的相互作用使它在左手和右手两个形态间相互转化，总体看起来它就是在以比光速慢的速度运动着，此时可以认为电子获得了质量。

所有这些基本粒子的质量都是通过与希格斯场相互作用获得的，相互作用的强度越强，粒子的质量就越大。
有趣的是，不同粒子与希格斯场的相互作用强度有着天壤之别：例如顶夸克的质量是电子质量的三十万倍！
中微子也是通过这种方式获得质量的，但其中包含了一些更复杂的细节，我们对它的理解也还不是很透彻。

尽管基本粒子都是通过希格斯场获得质量，可我们日常生活中的物体的绝大部分质量并非来源于此！
事实上，物体的大部分质量来自于原子核中质子和中子质量的总和，质子和中子是复合粒子而非基本粒子。

希格斯场是自然界中一个不基于规范对称性的全新的相互作用。
强相互作用是一种将夸克结合在一起，构成质子和中子的规范相互作用。

一个很有希望的暗物质粒子“候选者”是一种被弱相互作用支配的新粒子，它被称为“弱相互作用大质量粒子” (WIMP, Weakly Interacting Massive Particles)。
这种粒子的宇宙学丰度和实验观测相符，而且其他一些试图解释标准模型谜题的理论也很自然地预测了这种粒子的存在。

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

惯性质量与引力质量等效的原因是惯性也是由引力引起的，并且与宇宙中物质的总量有关。
为什么光速不变？因为由麦克斯韦方程推导出的真空中的光速是常数，与参照系无关。
狭义相对论提出了一个适用于所有运动的简单原则：任何物体穿越空间和穿越时间的合速度总是精确的等于光速。
这两种运动总是互补的，在空间的快速运动能减慢穿越时间的速度。 当物体在空间中以光速运时，时间就停止了。
1907 年的一天，爱因斯坦意识到加速与引力之间根本就是相似的，引力和加速运动是同一枚硬币的两面。
既然引力和加速是等价的，爱因斯坦领会到，引力本身不是别的，正是时空结构中的蜷曲和弯曲。
引力传播速度问题变成了空间的形状改变得有多快的问题。通过计算可以得出引力也是以光速传播。

“粒子的运动服从概率定律，而概率是按照因果律传递的。”
粒子虽然能观察，却不能预测；而波虽能预测，却又无法观察。
找出世界的简单明晰的图像，不仅是科学的目标，还是人们深层心理上的需要。

质量和能量的关系：质量就是锁闭起来的能量，而能量就是释放了的质量。
弦论能提出更合理的对量子力学的解释吗？
