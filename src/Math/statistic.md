# 统计学

### 基础公式

平均值(Mean)
$$\bar X=\frac{\sum_{i=1}^n{X_i}}{n}$$

方差(Variance), 也称 MSE(Mean Square Error) 各随机变量与平均值差值的平方和的平均数，先求差，再平方，再平均。
$$var(X)=\frac{\sum_{i=1}^n{(X_i-\bar X)^2}}{n-1}$$

标准差(Standard Deviation) 也称 均方差 RMSE(root mean square error) 是方差的算术平方根。
均方根 RMS(root mean square) 将所有值平方求和，求其均值，再开平方，就得到均方根值。
$$s=\sqrt{\frac{\sum_{i=1}^n{(X_i-\bar X)^2}}{n-1}}$$

协方差（Covariance）衡量两个变量的总体误差。
$$cov(X,Y)=\frac{\sum_{i=1}^n{(X_i-\bar X)(Y_i-\bar Y)}}{n-1}$$

The covariance Matrix for an n-dimensional data:

$$C_{n \times n}=[c_{ij}=cov(Dim_i,Dim_j)]$$

$$S=\frac{1}{n-1}\sum_{i=1}^n{(X_i-\bar X)(X_i-\bar X)^T}$$

正态分布中，平均值、中位数、众数(出现次数最多的)都是同一个值。
长尾分布中，分布曲线是不对称的。平均值远小于最大值，并且容易受杂点的影响，使用中位数更能反应实际情况。

Accuracy 精密度
Precision 准确度

The accuracy of derived model is a comparison of predicted and actual outputs.

Every datapoint has an uncertainty, or variance, associated with it. This is a representation of the precision of the input space.
We can translate the input variance into variance of our learned model parameters, our parameter variances will change as we fit our model to the input data. This becomes a good measure of model precision.
Now we know that our model can be trusted much more with certain inputs than with others. If we're trying to predict in a region outside of our input data range, we have a good idea of how much we can trust (or be skeptical of) the data.

准确度表示测量结果的正确性，精密度表示测量结果的重复性和重现性，精密度是准确度的前提条件。

加工精度是加工后零件表面的实际尺寸、形状、位置三种几何参数与图纸要求的理想几何参数的符合程度。理想的几何参数，对尺寸而言，就是平均尺寸；对表面几何形状而言，就是绝对的圆、圆柱、平面、锥面和直线等；对表面之间的相互位置而言，就是绝对的平行、垂直、同轴、对称等。零件实际几何参数与理想几何参数的偏离数值称为加工误差。

加工精度用公差等级衡量，等级值越小，其精度越高；公差等级从 IT01，IT0，IT1，IT2，IT3 至 IT18 一共有 20 个，其中 IT01 表示的话该零件加工精度最高的，IT18 表示的话该零件加工精度是最低的 ，一般上 IT7、IT8 是加工精度中等级别。

任何加工方法所得到的实际参数都不会绝对准确，从零件的功能看，只要加工误差在零件图要求的公差范围内，就认为保证了加工精度。

Statistics begins by assuming there is no effect.
Prior to collecting data, rules are chosen to decide whether whether the data are consistent with the assumption of no effect.
If the data are found to be inconsistent with the assumption, the assumption must be false and there is, in fact, an effect!

Failing to find an effect is different from showing there is no effect!
Showing that "there is no effect" means that all possibilities of practical importance have been ruled out.

classical statistics works by comparing study data to what is expected when there is nothing.
If the data are not typical of what is seen when there is nothing, there must be something!

相关性并不意味着因果关系。Association does not imply causation!

The rules for claiming causality vary from field to field.
The physical sciences seem to have the easiest time of it because it is easy to design experiments in which a single component can be isolated and studied.
Fields like history have the hardest time of it. Not only are experiments all but impossible, but observations often play out over generations, making it difficult to collect new data, while much of the existing data is often suspect.

We should not assume that what we don't understand is unimportant.

A good statistician will point out that causality can be proven only by demonstrating a mechanism. Statistics alone can never prove causality, but it can show you where to look.

Statistics is not just a collection of computational techniques. It is a way of thinking about the world.

## The Basics of Study Design

Focus is critical. There must be a clear goal in mind. Otherwise, time, energy, and money will be invested only to find that nothing has been accomplished.

1. There must be a fully formed, clearly stated, focused research question and SINGLE primary outcome measure.
2. The project must be feasible. This refers not only to resources (time and money), but also to whether there is agreement on the meaning of the research question and to whether everything that needs to be measured can be measured.
3. Every data item and every facet of the protocol must be carefully considered.
4. Keep it simple! Study only two groups at once, the research question is sharply focused.
5. Research has consequences! You must be aware of the possible consequences of your work.

A cross-sectional study involves a group of people observed at a single point in time by taking a slice or cross-section at a particular point in time.)

A longitudinal study involves the same individuals measured over time (or along the time line).

The only way to answer a longitudinal question is by collecting longitudinal data.
Effects seen over the short term may not continue over the long term.

Often, intervention trials are used to evaluate a single treatment. Things change even when no specific intervention occurs.
Placebo controlled means that the study involves two treatments--the treatment under investigation and an ineffective control (placebo) to which the new treatment can be compared.

Sample size calculations are necessary to design experiments that are large enough to produce useful information and small enough to be practical.
