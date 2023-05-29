# 编程

> 最好的工程师不是写代码最多的工程师，而是做出未来可以少写代码的决策的工程师。
> -- Dan Goldin

先思考再编程，想好了再动手，避免写到后面发现需要推倒重来。

不要在疲惫时写代码，真正好的代码是程序员完全进入状态的时候写出来的。

有一个诀窍，让我成为一个更好的程序员，那就是我常常休息，大量的休息，我的新想法都是在休息时产生的。

休息的时候，我阅读，大量阅读任何我有兴趣的内容，这样我才可能产生新想法。

Programming is not merely about language syntax and semantics, but more fundamentally about the iterative process of refining mental representations of computational problems and solutions and expressing those representations as code.

> “Everyone in this country should learn to program a computer, because it teaches you to think.” — Steve Jobs

> “If you can’t explain something in simple terms, you don’t understand it.”  如果你不能用简单的语言来解释某件事，你就无法理解它 — Richard Feynman

> “Just when you think you’ve successfully navigated one obstacle, another emerges. But that’s what keeps life interesting.
> 就在你认为已经成功跨域了一个障碍时候，另一个障碍有出现了，但这正是让生活变得有趣的地方。

> Each time, a little more of the competition falls away. Until all that is left is you: the best version of you.” — Ryan Holiday
> 每次，更多的竞争就会消失。直到你成为最好的自己。——瑞安. 霍利迪（障碍就是路）

“像程序员一样思考”, 是一种更有效的解决问题的方法。找到正确的框架，练习它。

"Mechanical Sympathy" comes from the great racing driver Jackie Stewart, who was a 3 times world Formula 1 champion. He believed the best drivers had enough understanding of how a machine worked so they could work in harmony with it.

Why does the software we use today not feel any faster than the DOS based applications we used 20 years ago??? It does not have to be this way. As a software developer I want to try and produce software which does justice to the wonderful achievements of our hardware friends.

## PL paradigms throughout history

• 1975: rise of systems languages
-- Efficiency first: we don’t have enough resources, carefully build a system

• 1995: rise of scripting languages
-- Productivity first: systems languages are too hard (and we have the resources), so quickly glue together a system

• 2015: rise of functional languages
-- Correctness first: scripting languages are too buggy, we need to know if our system works

## Simple, correct, fast: in that order

The single most important quality in a piece of software is simplicity. The reason is straightforward: if your solution is not simple, it will not be correct or fast.

Given enough time, you’ll find that all software which solves sufficiently complex problems is going to (1) have bugs and (2) have performance problems.

Software is a living thing! The complex problem comes later, and it’ll be better served by the composition of simple solutions than with the application of a complex solution.

理解、计划、拆分、探索、实践。

### 分而治之 (Divide and conquer)

### Naming things

> “There are only two hard things in Computer Science: cache invalidation and naming things.”
>
> – Popularly attributed to Phil Karlton

每一个变量、函数、文件名 – 就如同给你的孩子取名字一样认真去给他们取名字。也许你今天通过把它命名为 x 节省了 0.3 秒的时间，但是在接下来的一个月你将会花 2 天的时间来搞清楚 x 到底指代什么，然后再花 4 天做重构。好好想想，不要担心命名太长。

- Boolean variables, or functions that return a boolean value, should start with “is,” “has” or “should.”

```js
// Dirty
const done = current >= goal;
```

```js
// Clean
const isComplete = current >= goal;
```

- Functions should be named for what they do, not how they do it. In other words, don’t expose details of the implementation in the name. Why? Because how you do it may change some day, and you shouldn’t need to refactor your consuming code because of it. For example, you may load your config from a REST API today, but you may decide to bake it into the JavaScript tomorrow.

```js
// Dirty
const loadConfigFromServer = () => {
  ...
};
```

```js
// Clean
const loadConfig = () => {
  ...
};
```

### Closure

当一个函数能够记住并访问到其所在的词法作用域及作用域链，并能够在其定义的作用域外进行访问，此时该函数和其上层执行上下文共同构成闭包。

### DRY

DRY is an acronym that stands for “Don’t Repeat Yourself.” If you are doing the same thing in multiple places, consolidate the duplicate code. If you see patterns in your code, that is an indication it is prime for DRYing.

Clean code is a consistent style of programming that makes your code easier to write, read, and maintain.

You aren’t done just because your code “works”. Clean it up by removing dead code (zombie code), refactoring, and removing any commented-out code! Strive for maintainability. Ask yourself, “Will someone else be able to understand this code six months from now?”

A good developer, when faced with a situation where they have to do something more than once, will generally find an automated (or better) solution to complete the task at hand. Because you’re lazy, subscribing to clean-code techniques will decrease the frequency of changes from pull-request code reviews and the need to come back to the same piece of code over and over.

复用的本质是通过消除重复的方式。得到一系列可以复用的组件，从而在未来的开发工作中，更快速的响应需求变化。但如果为了复用，代码的可读性下降了，更难维护了，也就违背了复用的本质。

函数是最重要的实现代码复用的手段。

## SOLID 原则

S – Single Responsibility Principle 单一职责原则

O – Open/Closed Principle 开放 / 封闭原则

L – Liskov Substitution Principle 里氏替换原则

I – Interface Segregation Principle 接口隔离原则

D – Dependency Inversion Principle 依赖倒转原则

### Single Responsibility Principle

Use small functions, each with a single responsibility. Ensure that each function does one job and does it well. This could mean breaking up complex components into many smaller ones. This also will lead to better testability.

If you break your code into small modules, each with a single responsibility, it’s likely that you’ll never have to touch most modules again. There is time saved in “write it and forget it.”

Be on the lookout for leaky abstractions. In other words, don’t impose your internal requirements on consumers of your code.

### Clean Code

Clean code doesn’t (necessarily) take longer to write. Initially you may need to slow down before you can speed up, but eventually your pace will increase as you are writing fewer lines of code.

### Design

API 设计——库所提供的公共接口，向开发人员暴漏功能和特性——与 UI 设计一样重要。

应用程序的 UI 关注的是终端用户的体验，应用程序的 API 关注的则是开发人员的体验。就像我们重视 UI 的实用、简洁和优雅，我们也应该追求 API 的实用、简洁和优雅。

差劲的设计会导致浪费：浪费开发人员的时间，因为他们很难弄懂一个接口；浪费 API 作者的时间，因为她需要处理开发混乱带来的额外支持和返工。

良好的 API 设计可以实现抽象这一目标，同时也应该是自描述的。如果一个 API 被良好地设计，用户可以快速直观地利用你的工作成果，而且不需要经常参考手册和文档，不需要频繁访问技术支持和问答网站。对于需要开发人员花费大量时间来开发的特性，你也可以把它们封装起来以节省开发人员的时间。良好的设计不仅可以节省开发人员的时间，也让他们看起来更加聪明和可靠。

我们可以把艺术领域中常用的的 4 项设计原则应用到 API 设计中：

- 一致 & 协调
- 平衡
- 相衬
- 重点突出

一致性是一件作品背后不可或缺的概念，使得设计者可以把各种事物汇集成一个连贯的整体。另一方面，协调性则是指作品中相似元素的布局，使得作品从整体上产生一种简洁的感觉。一致性和协调性的目的在于向 API 新手传达友好和舒适的感觉。虽然 API 的功能不同，但是通过相同或相似的 “方言”，可以大大降低开发人员采用新工具的门槛。

第二个原则是平衡，布置元素时要不能让作品的某个部分过于出彩而是其他部分黯然失色，或者让人感觉作品不稳定。在艺术上，平衡与视觉权重（吸引力）有关。在 API 设计中，平衡特指代码的视觉权重和可预测性。

第三个原则是相衬，它用来衡量作品中元素的大小和数量。并不是说小 API 就是好 API，相衬性所衡量的大小与 API 的用途（功能）有关。一个具备相衬性的 API，它的外观应该与它的能力范围相匹配。

在艺术上，突出重点是指通过使用对比，使作品的某个方面凸显出来成为焦点。在许多 API 中，焦点可能是锚定库的入口方法或主方法。突出重点的另一个示例可能是 “链式” 或流式 API，它可以突出库所使用的中心对象。

### 十步学习法

第一步：了解全局

第二步：确定范围

第三步：定义目标

第四步：寻找资源

第五步：创建学习计划

第六步：筛选资源

第七步：开始学习，浅尝辄止

第八步：动手操作，边玩边学

第九步：全面学习，学以致用

第十步：乐为人师，融会贯通

### 任务分解方法：

1. 定义问题
2. 把大问题分解成小问题
3. 为每一个单独问题设计算法
4. 把解决方案组合成系统

## 元编程：用程序来生成程序

That's the beauty of new things: there's always a new one coming along. Don't let the pursuit of new, shiny things accidentally become your goal. Avoid becoming a magpie developer. Be selective in your pursuit of the shiny and new, and you may find yourself a better developer for it.

### Tidying Up Your Code: KonMari Style

The six basic rules of tidying.

RULE 01 定下整理的决心
Commit yourself to tidying up.

RULE 02 想象自己的理想生活方式
Imagine your ideal lifestyle.

RULE 03 舍弃是整理的第一步
Finish discarding first.

RULE 04 按类别整理而不是按照地点
Tidy by category, not by location.

RULE 05 按照正确的顺序
Follow the right order.

RULE 06 这件物品让你怦然心动吗？
Ask yourself if it sparks joy.

Konmari 法则中最重要的一点就是：只留下让你怦然心动的物品。

## memory model

- Global Allocation:

const is a fixed value; the compiler is allowed to copy it wherever useful.
static is a fixed reference; the compiler will guarantee it is unique.

const values are loaded into memory as part of your program binary. Getting the address of a const value is possible, but not guaranteed to be unique (because the compiler can choose to copy values).

static variables are globally unique locations in memory.

- Heap Allocation:

The heap is used in two situations; when the compiler is unable to predict either the total size of memory needed, or how long the memory is needed for, it allocates space in the heap.

When a smart pointer is created, the data it is given is placed in heap memory and the location of that data is recorded in the smart pointer. Once the smart pointer has determined it’s safe to deallocate that memory (when a Box has gone out of scope or a reference count goes to zero), the heap space is reclaimed.

Collection types use heap memory because their contents have dynamic size; they will request more memory when needed, and can release memory when it’s no longer necessary. Collections are smart pointers for many objects at a time.

- Stack Allocation:

Stack allocation will be used for everything that doesn’t involve “smart pointers” and collections.

stack memory can be managed far faster in both the short- and long-term than heap memory.

When writing performance-sensitive code, there’s no alternative to measuring your code. If you didn’t write a benchmark, you don’t care about it’s performance You should never rely on your instincts when a microsecond is an eternity.

## 逻辑编程（logic programming）

在像 Prolog 这样的逻辑式语言里面，“未知数” 是可以被作为一个正常的值来进行计算的。它们可以被传递到其它函数里，可以被放进数据结构，可以进行复杂的逻辑组合操作。

逻辑式程序中一般会有一个（或者多个）“目标”（goal）。目标一般是一个判断表达式，也就是说它的值是布尔类型（boolean）。逻辑语言的运行系统进行 “反向计算”，找到未知数的值，使得目标的值为 “真”（true）。

机器学习的 weight 对应于逻辑编程的 “未知数”（比如 X），机器学习中的误差函数（loss function）对应于逻辑编程的 “目标”（goal）。只不过逻辑编程的 goal 是个等式，而机器学习的 loss function 是个函数。机器学习的 weight 本质就是 “未知数”，给它们一些随机的初始值，让系统开始正向计算，直至遇到 loss function，然后掉头回去调整未知数的值。

逻辑编程系统会为你选择未知数的值，从而精确地 “满足” 这个 goal。而机器学习的目标呢，是要为你选择未知数的值，最小化这个 loss function，使得误差最小。所以，机器学习可以被看成是 “在连续空间中的近似的逻辑编程”，而逻辑编程可以被看成是 “在离散空间中的精确的机器学习”。

逻辑编程有 “反向计算”，机器学习有 “反向传递”(back propagation)，而它们的工作方式，有着惊人的相似之处。只不过机器学习因为是连续空间的，所以需要使用微积分的原理，而不只是简单的逻辑组合。

实际上逻辑编程必须先进行正向计算，构造出含有未知数的结构，然后进行所谓 “unification”，求出未知数的值。而机器学习也类似，你必须进行一遍正向计算（forward pass），然后才能进行 back propagation，求出导数，并且更新 “weight” 的值。由于机器学习解决的是连续的数值问题，机器学习的 “模型” 一般要很简单才行，否则很可能出现学习不收敛的情况。

机器学习的各种框架（framework）可以看成是新的编程语言，它们不同于 Python 或者 C 一类的过程式语言，而更像 Prolog 这样的逻辑式语言。这些语言会自动对代码求导，优化未知参数，使得误差最小。动态语言和静态语言的差别，对应着 Pytorch 和 TensorFlow 的动态计算图和静态计算图的区别。

目前机器学习的一些发展趋势：

1. Feed-forward 网络，比如 CNN 一类的，对应了编程语言中最简单的表达式，或者叫 “纯函数”。其中没有递归，也没有副作用。它只能处理图像一类具有固定长度的数据。
2. RNN（LSTM）对应的是程序语言里含有单个递归（循环）的函数。由于递归函数对应的是 “递归数据结构”，这就是为什么 RNN 可以处理文本这类线性 “链表” 数据。
3. Neural Turing Machine 及其后续的研究 Differentiable Neural Computer，试图把更广阔的编程概念引入到机器学习里面，处理任意复杂的数据结构，比如图结构。

库和框架的一个区别是，一次可以使用多个库，但是框架一次只能使用一个。

这就是为什么我不使用框架的原因。一旦用了一个框架，就无法再用另一个框架了，移植的成本太高了。使用库就没有这个问题。

团队每次使用框架时，都会冒风险。风险在于，框架可能在你的软件之前"消失"，从而给开发人员带来沉重的负担。
