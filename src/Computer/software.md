# 软件工程

> 一个可运行的复杂系统，总是从一个简单系统演变而来的。似乎可以因此推断：从头开始设计一个复杂系统，永远不会奏效，必须从一个简单系统开始设计。

-- 《加尔定律》

主要的软件领域：

- 操作系统
- 编译器、调试器
- 文本编辑器
- 浏览器引擎
- 游戏引擎
- 数值计算、符号计算
- CAD 内核
- 图像、音频、视频编码解码
- 字体、排版
- 压缩算法
- 加密算法
- 图形界面
- 网络协议
- 工业软件

《软件设计的哲学》（A Philosophy of Software Design）

一、什么是复杂性

Ousterhout 教授认为，软件设计的最大目标，就是降低复杂性（complexity）。 所谓复杂性，就是任何使得软件难于理解和修改的因素。

Complexity is anything that makes software hard to understand or to modify.

复杂性的来源主要有两个：代码的含义模糊和互相依赖。

Complexity is caused by obscurity and dependencies.

模糊指的是，代码里面的重要信息，看不出来。依赖指的是，某个模块的代码，不结合其他模块，就会无法理解。

Obscurity is when important information is not obvious.

Dependency is when code can't be understood in isolation.

复杂性的危害在于，它会递增。你做错了一个决定，导致后面的代码都基于前面的错误实现，整个软件变得越来越复杂。"我们先把产品做出来，后面再改进"，这根本做不到。

Complexity is incremental, the result of thousands of choices. Which makes it hard to prevent and even harder to fix.

二、复杂性的隔离

降低复杂性的基本方法，就是把复杂性隔离。"如果能把复杂性隔离在一个模块，不与其他模块互动，就达到了消除复杂性的目的。"

Isolating complexity in places that are rarely interacted with is roughly equivalent to eliminating complexity.

改变软件设计的时候，修改的代码越少，软件的复杂性越低。

Reduce the amount of code that is affected by each design decision, so design changes don't require very many code modifications.

复杂性尽量封装在模块里面，不要暴露出来。如果多个模块耦合，那就把这些模块合并成一个。

When a design decision is used across multiple modules, coupling them together.

三、接口和实现

模块分成接口和实现。接口要简单，实现可以复杂。

Modules are interface and implementation. The best modules are where interface is much simpler than implementation.

It's more important for a module to have a simple interface than a simple implementation.

好的 class 应该是"小接口，大功能"，糟糕的 class 是"大接口，小功能"。好的设计是，大量的功能隐藏在简单接口之下，对用户不可见，用户感觉不到这是一个复杂的 class。

最好的例子就是 Unix 的文件读写接口，只暴露了 5 个方法，就囊括了所有的读写行为。

四、减少抛错

异常是大量复杂性的来源，有些软件设计者喜欢抛错，一遇到问题，就抛出一个 Exception。这也导致了复杂性，用户必须面对所有的 Exception。"反正我告诉你出错了，怎么解决是你的事。"

正确的做法是，除了那些必须告诉用户的错误，其他错误尽量在软件内部处理掉，不要抛出。

Tcl 语言的最初设计是，unset() 方法用来删除已经存在的变量，如果变量不存在，该方法抛错。Ousterhout 教授说，这个设计是一个错误，完全不应该抛错，只要把 unset() 定义成让一个变量不存在，就解决问题了。

另一个例子是，Windows 系统不能删除已经打开的文件，会有错误提醒。这也是一个设计错误，有些用户实在删不掉这些文件，不得不重启系统。Unix 的做法是，总是允许用户删除文件，但是不清理内存，已经打开的文件在内存里面继续存在，因此不会干扰其他程序的运行，那些程序退出保存文件的时候，发现文件不存在才会报错。这个设计比较好。

康威定律可总结为四个定律：

第一定律 组织沟通方式会通过系统设计体现出来。
第二定律 时间再多一件事情也不可能做的完美，但总有时间做完一件事情。
第三定律 线型系统和线型组织架构间有潜在的异质同态特性。
第四定律 大的系统组织总是比小系统更倾向于分解。

设计的第一原则，也是设计的本质：取舍（trade off）。

解耦是推动软件架构变革的原动力，但解耦只能是第二原则。

重构阶段
阶段 1：科学怪人的怪兽（Frankenstein’s Monster）
阶段 2：深度清理
阶段 3：管道（pipeline）重构

When people are actually using it, and interested in it, it started to have a life of its own. People started sending patches, and the system begin growing.

GPLv2 is pretty much the perfect balance of "everybody works under the same rules", and still requires that people give back to the community ("tit-for-tat").

### Single Writer Principle

For any item of data, or resource, that item of data should be owned by a single execution context for all mutations.

### Event Driven Services

Centralize an immutable stream of facts. Decentralize the freedom to act, adapt and change.

Events trigger processing. Events provide far less opportunity for services to couple themselves to one another, and flipping flow-control to the receiver makes for better separated concerns and better pluggability.

### Project Management

- People first: people are more valuable than schedules; keeping people healthy, happy, and productive is the most important aspect of managing a project.
- Open communication: we should be as open as possible as early as possible with communication about projects, even when the nature of the project means we can't be open with all development.
- Get feedback early and set expectations about the kind of feedback which is useful. We have ongoing problems in the Rust community where (mostly) well-intentioned feedback from the community becomes overwhelming to the point of harassment; we do not have a solution to this.
- Be prepared to manage feedback, in particular by having enough people available to respond.
  Recognize the complexity of projects and ensure appropriate project management.
- Projects should have clear ownership.
- Large projects should not be scheduled to finish at the same time.
- Work iteratively, rather than going for 'big bang' releases.
- Consider ongoing maintenance: how much is there to do? Who will do it? Failing to consider this means there is more pressure on the initial release.

### 代码审查（Code Review）

> Given enough eyeballs, all bugs are shallow. -- Linus

代码审查是一个过程，即代码只有经过非作者本人评审后才能进入代码仓库。
代码审查的目的是保证代码质量，代码质量是软件系统的内在质量。
《代码大全》第二十章中中给出了代码质量的特性：

• 可维护性（Mantinability）
• 灵活性（Flexibility）
• 可移植性（Portability）
• 可重用性（Reusability）
• 可读性（Readability）
• 可测试性（Testability）
• 可理解性（Understandability）

### 扩展（scaling）

《加速：构建和扩展高性能技术组织》
《规模：生物，城市和公司的普遍法则》

大项目的开发效率不高，根本原因是软件规模的增长，必然使得代码和团队变得笨重。
解决这个问题，要从代码和团队两方面着手。

代码层面的解决方法是，将软件解耦，拆分成组件或者模块，防止各个部分紧密地耦合在一起。每个组件和模块，都可以独立开发，通过公开的接口被其它部分调用。

大团队也应该遵循类似的原则，进行解耦。

- 每个子团队都可以独立运作，不依赖外部人员。

子团队应该是一个小型的全功能软件开发组织。每组负责一个全流程的软件大功能，设计、编码、测试、部署、支持等人员都在同一组。这样才能做到解耦，以及独立的交付和重构。每组内部使用什么工具、如何实现某个功能，都是自己决定，各组之间不需要共享内部细节，也不依赖别组的工作。

- 子团队内部的运作，不需要被外部知道。
- 子团队之间的协调，应该按照公开的协议和规则，最好能够自动完成，避免私下协商。
- 每个子团队最好不要超过 5 个人。
- 大团队应该保障子团队的自主权，按照子团队提供的功能和商业价值，进行资源分配。
- 软件架构师的关注点，不应该是团队使用的工具和技术，而是各种服务与整个系统运行状况之间的协议和通信，保证代码和团队可以正确解耦。
- 理想情况下，代码解耦与团队解耦保持一致，形成一对一的关系，一个子团队负责一个独立的模块。实际运作中，一个子团队负责几个模块也可以，但是一个模块不能由多个子团队来参与。
- 通信（模块之间的、子团队之间的）尽量规范化，争取做到过程简单、文档充分，最好有规范的 API，这样无需任何人员交流，就能建立通信。
