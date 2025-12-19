[神经网络常用函数](https://www.desmos.com/calculator/gfqditn7wu)

## 感知器
感知器模型是一个线性分类器。它的目标是找到一个“超平面”（在二维空间中是直线，在三维空间中是平面，或在更高维空间中的类似物），用以区分两类数据。
对于一个数据集来说，若能找到一个超平面将所有数据点正确分类，则称该数据集是线性可分的。
Rosenblatt 在1960年证明了感知器收敛定理。该定理指出，如果一个数据集可以线性分离，那么感知器学习算法将在有限步数内找到解决方案。但如果数据集不是线性可分的，感知器学习算法可能无法找到合适的解决方案或收敛。
数学上，感知器模型可以表示为：
$$
y=f(w·x+b)
$$
其中，x 是输入向量；w是权重向量；b是偏置项；而f是激活函数。在感知器的情况下，激活函数是一个阶跃函数，它将输出映射为 1 或 0，代表两个类别。

感知器模型可以用来表示逻辑门，如与（AND）、或（OR）和非（NOT）。
单个感知器无法模拟 XOR 门，因为 XOR 门不是线性可分的。相反，必须使用多层感知器或感知器的组合来解决 XOR 问题。
这种感知器与逻辑门之间的联系表明，神经网络可以执行计算，并且有潜力模拟复杂系统。

感知器模型使用阶跃函数作为其激活函数，而逻辑回归使用逻辑（Sigmoid）函数。这种差异导致感知器有一个二元输出（0 或 1），而逻辑回归则生成一个概率值（在 0 和 1 之间），表示实例属于某个特定类别的可能性。
由于基于概率并且可以模拟非线性决策边界，逻辑回归更为可靠，并且能够处理更广泛的问题。然而，在某些情况下，尤其是处理线性可分数据时，感知器模型可能更易于使用且消耗更少的计算资源。

## 多层感知器（MLP）
多层感知器（MLP）的引入标志着人工神经网络的重大进步，MLP 由多个类似感知器单元的层组成。
给定足够数量的隐藏层和神经元，MLP 可以逼近任何连续函数。
通过使用反向传播算法，MLP 可以被训练来解决更复杂的任务。



过去 50 年里主导人工智能领域的三种类型的机器学习模型，包括概率图模型、支持向量机、和深度神经网络。
长期以来，Function Learning 基本被简单等同于连续函数拟合和回归任务。但其实在心理学和认知科学中，研究者们也使用 Function Learning 的概念来模拟人类和其他智能主体的刺激-反应关系的心理诱导过程，其过程涉及知识获取、信息处理和推理等一系列复杂的过程。

1980年代末，Cybenko定理证明了任何连续函数都可以用神经网络来逼近，并未明确指出神经网络与传统方法（如多项式）之间的本质区别。
1993年，Barron提出了一个真正的正确观点，他证明了神经网络逼近函数时，其收敛速度与维数无关。以多项式为例，要将误差降低10倍，所需的自由度数量需要指数级增长，这就产生了维数灾难。而神经网络则不受此限制，其性能与维数无关，这为我们提供了一个正确的出发点，突显了神经网络在处理高维问题上的优势。

深度学习有潜力解决维数灾难问题，我们需要从数学上更深入地理解深度学习与传统多项式方法之间的区别。

在科学领域，许多问题和困难都源于自由度过多，例如量子力学、分子动力学、蛋白质折叠等典型的多体问题。

除了维数灾难问题，还有其他挑战，例如记忆灾难。在处理时间序列数据的时候，对记忆的依赖是一个主要问题。
传统的循环神经网络在这方面存在局限，而Transformer架构则没有这样的困难。

BERT和ChatGPT的预训练模型是两个主要的解决方案。BERT通过“填空”的方式进行预训练，而ChatGPT则通过“预测下一个词”的方式。
ChatGPT的“预测下一个词”模型不仅具有通用性，还是一种生成模型。

## 常用激活函数

[激活函数合集](https://www.desmos.com/calculator/immjjlf0im)

1. 分段线性族 (Piecewise-Linear)

- 修正线性单元 ReLU (Rectified Linear Unit)
$$\text{ReLU}(x) = (x)^+ = \max(0, x)$$

- Leaky ReLU: 
$$ \text{LeakyReLU}(x) = \max(\alpha x,x) , \alpha \in (0,1) $$
$$ \text{LeakyReLU}(x) = \begin{cases} x & \text{if } x \geq 0 \newline \alpha  x & \text{otherwise} \end{cases} $$

- 参数化修正线性单元 Parameterized Rectified Linear Unit（PReLU），α 是一个可学习的参数
$$ \text{PReLU}(x) = \max(\alpha x,x) , \alpha \in (0,1) $$
$$ \text{PReLU}(x) = \begin{cases} x & \text{if } x \geq 0 \newline \alpha x & \text{otherwise} \end{cases} $$

- 高斯误差线性单元（GELU）
$$ \text{GELU}(x) = x \cdot \Phi(x) = x \cdot \frac{1}{2}\left(1 + \text{erf}\left(\frac{x}{\sqrt{2}}\right)\right) $$

2. 平滑 S 型族 (Smooth Sigmoidal)

- Sigmoid 函数
Sigmoid 的输出在 $[0, 1]$ 之间，模拟一个 “开关”：0 代表 “完全关闭/忘记”，1 代表 “完全打开/通过”。

$$ \text{sigmoid}(x) = \frac{1}{1 + \exp(-x)} $$
$$ \text{log\_sigmoid}(x) = \log\left(\frac{1}{1 + \exp(-x)}\right) $$
$$ \text{hard\_sigmoid}(x) = \max(0, \min(1, \alpha x + \beta)) $$

- 双曲正切函数（Tanh）
Tanh 的输出在 $[-1, 1]$ 之间，它是一个以 0 为中心的 “有界” 范围。这非常适合用来更新 “记忆细胞” 的内容，既可以增加记忆（正值），也可以减少记忆（负值），而且不会导致数值爆炸。

$$ \text{tanh}(x) = \frac{\exp(x) - \exp(-x)}{\exp(x) + \exp(-x)} $$
$$ \text{log\_tanh}(x) = \log\left(\frac{\exp(x) - \exp(-x)}{\exp(x) + \exp(-x)}\right) $$

3. 高性能平滑族 (High-Performance Smooth)

将输入（或其变体）同时用作 “内容” 和 “门控信号”，实现复杂的非线性。

- 平滑线性单元（SiLU 或 Swish）: 
$$Swish(x) = x \cdot \text{Sigmoid}(\beta x)$$
$$ \text{SiLU}(x) = x * \sigma(x) = \frac{x}{1 + \exp(-x)} $$

- Mish 函数
$$ \text{Mish}(x) = x \cdot \tanh(\text{Softplus}(x)) = \tanh\left(\log(1 + \exp(x))\right) $$

4. 周期/局部族 (Periodic / Local)
sin (正弦): $f(x) = \sin(x)$
Gaussian (高斯): $f(x) = e^{-x^2}$

- Softplus 函数
$$ \text{softplus}(x) = \frac{1}{\beta}\log(1 + \exp(\beta x)) $$

- Softmax 函数
$$ \text{softmax}(x_i) = \frac{\exp(x_i)}{\sum_j \exp(x_j)} $$

通俗地说， softmax 函数的最大值输出，就是在最不靠谱的条件下的最靠谱估计。 如果这个估计也靠谱的话，那么就真的很靠谱了。

Softplus（σ(z)=ln(1+e^z) ）

ELU (Exponential Linear Unit) σ(z)=α(min(0,z)+max(0,z))

SELU (Scaled Exponential Linear Unit) σ(z)=α(min(0,z)+max(0,z))
