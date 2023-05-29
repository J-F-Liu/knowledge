# 程序设计

> 要么是用户控制程序，要么是程序控制用户。
> -- 理查德・斯托曼

> 最好的程序员不是善于编写复杂代码，而是有能力为复杂的问题提出简单的解决方案。只有糟糕的程序员，才会对简单的问题提出复杂的解决方案。

> "减少人类的苦难"，对我来说就是软件价值的核心。我过去和现在所做的工作都以此为目标。

> 程序员对渐进式翻新不感兴趣：修修补补、改进、在花坛种上绿植...... 他们不想做这些事，他们总是想扔掉旧代码并重新开始，原因并非是认为旧代码一团糟，而是编程的一个基本法则：阅读代码比编写代码更难。

> Programming is about solving technical problems, but how you solve them, and how you think about them is important too, and it's one of those things you start to recognize over time: certain people have that "good taste" thing and pick the "right" solution.
> I don't want to claim that programming is an art, because it really is mostly just about 'good engineering'. I'm a big believer in Thomas Edison's 'one percent inspiration and ninety-nine percent perspiration' mantra: it's almost all about the little details and the everyday grunt-work. But there is that occasional 'inspiration' part, that 'good taste' thing that is about more than just solving some problem - solving it cleanly and nicely and yes, even beautifully.
> I think one of the big successes of Linux is having literally hundreds of maintainers around, all with that hard-to-define "good taste", and all people who maintain parts of the kernel.
> -- Linus

> "Recursion! The cause of, and solution to, all of life's problems!"

> There's a big difference between solving a problem and making a problem go away.

> If you want everything to be familiar, you'll never learn anything new. - Rich Hickey

> There's no such thing as a perfectly intuitive programming language because algorithmic thinking isn't something that comes to us intuitively. That's why the first language is always the hardest.

> Relying on the programmer to always read, comprehend, and remember the documentation – and then do everything right, every time – is how we get bugs.

> “Indeed, the ratio of time spent reading versus writing is well over 10 to 1. We are constantly reading old code as part of the effort to write new code. …[Therefore,] making it easy to read makes it easier to write.”
>
> Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship

编程是思考，而不是打字。多年编程后，我时常觉得自己打字太多，思考太少。

Coding is to programming what typing is to writing.
Writing is something that involves mental effort you're thinking about what you're going to say.
In the same way, programs are built on ideas, they have to do something and what they're supposed to do is liking what writing is supposed to convey.

If people are trying to learn programming by being taught to code, well they are being taught writing by being taught how to type and that dosn't make much sense.

When you write an algorithm you need to have a proof that it's correct, if you are proving things that means mathematics.

> Leslie Lamport

Thinking what program is supposed to do mathematically, write down the ideas that go into the program before you do any coding.

I find that the best way to describe a solution is often to just write the snippet of code - maybe not the whole thing - and just make it very concrete that way.

Programming is a tool to solve problems that you have in the domain of computers.

The purpose of a program is, and ought to be, something that transforms data into other forms of data.

A Value is a datum with an associated type.

A (Data) Type is an attribute of a value which encodes information about how the data value can be operated upon.

An Object is a value with associated behaviour, and thus implies it has agency.

Most programming languages are partly a way of expressing things in terms of other things and partly a basic set of given things.

### Composition is the Essence of Programming

What is programming?
At the most basic level, programming is about telling the computer what to do.
We are solving a non-trivial problem，if it were trivial, we wouldn’t need the help of the computer.

And how do we solve problems?
We decompose bigger problems into smaller problems, we write code that solves all the small problems.
And then comes the essence of programming: we compose those pieces of code to create solutions to larger problems.
**Decomposition wouldn’t make sense if we weren’t able to put the pieces back together.**

Our brains can only deal with a small number of concepts at a time.
We are unable to deal with the soup of objects or the spaghetti of code.
We need structure not because well structured programs are pleasant to look at,
but because otherwise our brains can’t process them efficiently.

Once a chunk is implemented, we can forget about the details of its implementation
and concentrate on how it interacts with other chunks.

An object in category theory is an abstract nebulous entity.
All you can ever know about it is how it relates to other objects.

The moment you have to dig into the implementation of the object in order to understand
how to compose it with other objects, you’ve lost the advantages of your programming paradigm.

### Types Are About Composability

In programming we pass the results of one function to another.
The data types of the two ends must fit for the composition to work.

The simplest intuition for types is that they are sets of values. Sets can be finite or infinite.

### Describing the semantics of a language

Operational semantics describes the mechanics of program execution by defining a formalized idealized interpreter.
It’s very hard to prove things about programs using operational semantics.

In denotational semantics every programming construct is given its mathematical interpretation.
With that, if you want to prove a property of a program, you just prove a mathematical theorem.
Thus it’s possible to perform formal proofs of correctness of software.

### The principle

The concept of co-location can be boiled down to this fundamental principle:

> Place code as close to where it's relevant as possible

You might also say: "Things that change together should be located as close as reasonable."

### API

Programming involves using and creating APIs. When we're creating a new API, we typically think in terms of defining functions to allow users to work with our library.
A different perspective is to think of these APIs as little languages, or domain-specific languages.

### Learning

Personally, I cannot learn a new language from simply watching youtube videos, but rather through seeking out solutions for myself, making mistakes, and feeling humbled by the process.

### Pure and Dirty Functions

Functions that always produce the same result given the same input and have no side effects are called pure functions.

Computational effect can be mapped to monads. Monads let us model all kinds of effects using only pure functions.

像奴隶一样工作，像国王一样命令，像神一样创造。（康斯坦丁·布朗库西，1876 年－1957 年，现代主义雕塑先驱）

As a developer, we always like to choose the best thing among several choices available.

The code editor is an application that enables the programmer to write and manipulate the source code.

IDE stands for Integrated Development Environment. It is a Graphical User Interface (GUI) based software which allows the programmers to write, debug, release, and deploy their code.

Syntax highlighting means that the editor displays the text, more specifically, the source code in different colors according to the programming language being used.

Debugging is the process of finding and removing bugs from a program.

## Data Structures are key to a good program

> Data dominates. If you’ve chosen the right data structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming. -- Rob Pike 1989

> I’m a huge proponent of designing your code around the data, rather than the other way around, and I think it’s one of the reasons git has been fairly successful… I will, in fact, claim that the difference between a bad programmer and a good one is whether he considers his code or his data structures more important. Bad programmers worry about the code. Good programmers worry about data structures and their relationships. -- Linus Torvalds 2006

Good data structures makes coding easy to design and maintain, whereas the best code in the world cannot make up for poor data structures.

计算机科学中的一切都循序渐进的. 知识点是循序渐进的，略过前面的知识点无异于搭建空中楼阁.

如果当前你正在学习的知识点对你而言很无厘头, 请停留在当前位置, 暂不要进行下一个知识点。
如果您使用的辅导资料(或书籍)没有充分诠释该知识点, 那么务必去寻找其他适合您的资源。
请避免过多负面的自省，不要被各种问题打击到怀疑人生, 坚持下去。

SPOT（Single Point Of Truth，单点事实）。代码需要修改时，你只需要在一个地方修改，而不必改动多个地方。

RECOMMENDATIONS
R1. Never use global variables
R2. Declare single-purpose variables
R3. Declare variables close to their use
R4. Keep code blocks small
R5. Use variables close to their declaration
R6. Use no more than two nesting levels

REPL: read-eval-print loop

[程序员的誓言](https://blog.cleancoder.com/uncle-bob/2015/11/18/TheProgrammersOath.html)

为了捍卫和维护计算机程序员的职业荣誉，我承诺，尽我所能和判断力：

1、我不会产生有害的代码。

2、我制作的代码永远是我最好的作品。我不会故意允许在行为或结构上有缺陷的代码。

3、每次发布时，我都会生成一个快速、可靠、可重复的证据，证明代码的每个元素都应该正常工作。

4、我将经常发布小版本，这样我就不会妨碍其他人的进展。

5、我会抓住每一个机会，无畏地，不懈地改进我的代码。我永远不会损害它们。

6、我将尽我所能保持自己和他人的生产力。我不会做任何降低生产力的事情。

7、我将继续确保支持其他人的工作，并且他们也可以支持我的工作。

8、我将对幅度和精度做出诚实的估计。我不会作出做不到的诺言。

9、我将永远不会停止学习和改进我的手艺。

优秀的程序员会在项目开始前，主动帮助产品把需求明确细化，这样可以避免开发阶段的无效的加班和工作。

提交代码后，谷歌内部有两次代码审查。第一次审查是功能审查，确保代码按照预期工作；第二次审查是可读性审查，确保代码是可读的，并且易于理解和维护。

The following are the characteristics of clean code:

- It must be readable.
- This must be elegant.
- They must be easy to understand and follow the Single Responsibility Principle (SRP).
- Clean Code must be easy to understand, easy to modify, and easy to maintain.
- Clean must run tests as per the test strategy.

Starting a new project is exciting. You get to try the new database, the new framework, the new architecture, the new everything.
But every new tool introduces a risk. And those risks compound. That’s why I believe that you should choose boring technology for most of your stack and only allow a meagre novelty budget.

There are many stories of applications that are now impossible to maintain because someone decided that the latest NoSQL database, framework, or language would be perfect for the new project. That person has now left and no one knows how to keep the application alive. Luckily, Rust is a programming language for the next 40 years.

The database / business logic split, which is arguably the most successful example of process separation. In this model, the database is responsible for performance and integrity, and the business logic is in a separate process, so it can safely do things like crash and hang.

## Language wars

As an aside, thinking of languages as platforms also explains language flame wars.

Your productivity in any language is directly proportional to your time and effort investment in it. It’s in your best interests to pick the language that’s likely to thrive and spend time learning it’s ins and outs. On the flip side, betting on a horse that doesn’t win could mean the loss of months or years of effort. This is why people evangelize the platforms they’re invested in - convincing other people to join improves the health of the platform, increasing their return on investment.

This evangelizing can sometimes become contentious if others perceive it as an attack on their platform. People defend their language mostly because they don’t want to see it lose popularity. If it did, their language’s viability is threatened and their investment is in jeopardy. It’s also partly because they’ve spent so long on it that it’s become a part of their identity.

That’s something for us to keep in mind as we advocate for a language we like.

#### C 语言

Language theorists can occasionally refer to C as a “big macro assembler”, the only thing abstracted away is really the raw instruction set.

C provided freedom, where high-level languages were considered as straight-jackets enforcing unwanted discipline. It was an invitation to use tricks which had been necessary to achieve efficiency in the early days of computers.

We can see why an efficiency-oriented operating system kernel such as Linux will tend toward C.

## 标准库

数据结构
文本处理
时间日期
进程线程（环境变量、命令参数）
终端界面
图形界面
文件目录
网络连接

Change is constant.
Your product is an asset, but code is a liability.
Duplication is less costly than premature abstraction.
The only true authority stems from knowledge, not from position.
Writing throwaway code to explore a problem space is underrated.
A good design is one in which you can change your mind without changing too much code.

Software architecture probably matters more than anything else. A shitty implementation of a good abstraction causes no net harm to the code base. A bad abstraction or missing layer causes everything to rot.

One aspect of software development is that software developers are expected to constantly be learning new things.

## Debugging

When we write code we make assumptions, and sometimes we assume wrong. This leads to bugs, which we then track down and fix. This is what we call "debugging", and is a core part of programming.

### Debugging: The 9 Indispensable Rules

1. Understand the system

It’s important to have knowledge of what the software is supposed to do, how it’s designed, and in some instances, why it was designed that way.
Know how to work with the debugging tools, they are your eyes and ears into the system, take your time to learn them, it will pay off greatly.

2. Make It Fail

Reproducing the bug allows us to see the failure, knowing under precisely what conditions the failure occurs can give us a better understanding of the possible causes, and also is important to know how to make it fail in order to ensure that you’ve fixed the bug after having implemented the solution.

3. Quit Thinking and Look

Don’t guess how something is failing and then try to implement the fix to your guess, it takes time, money and may break something else in the system, instead, look and find the cause of the bug.

Read the error message, thoroughly read it and try to understand what exactly is going wrong, perhaps google and see what the error message is about, that can give you another clue to what could be causing the bug to occur. 🔍

4. Divide and Conquer

We divide the code in half, then identify in which half the problem is, and do the same thing to the half where the problem was. We continue doing this till we’ve narrowed down exactly where the bug gets caused.

5. Change One Thing at a Time

If a change doesn’t seem to have an effect, undo it right away, don’t let it stay there while you continue looking for the cause of the bug.

6. Keep an Audit Trail

When trying to find the cause of the bug, write down what you did, what order you did it in, and what happened as a result. It’s important to keep track of each step, in order to determine where to focus on during debugging. ✍️

7. Check the Plug 🔌

Checking the plug is about checking that things actually work as they should, things we expected to work in a way. It seems like a silly thing but happens a lot. It can even be in the tools you are using, the framework, library, compiler, debugging tools, linter, etc.

8. Get a Fresh View

Sometimes something that would’ve taken us hours to solve can take us minutes to solve when asking a teammate for help. Someone who comes at the problem from a different angle can give us great insights and new approaches to try. 👀

9. If You Didn’t Fix It, It Ain’t Fixed

When you think you’ve fixed an engineering design, take the fix out. Make sure it’s broken again. Put the fix back in. Make sure it’s fixed again.

## Experimentation and Iteration

We didn't just build things once and assume that was the best we could do.

The spirit of open source is the contribution rather than request. When everyone is using and benefiting from open source codes, you should respect these codes and the communities behind them in a way, you should be in awe of the spirit of open source.

## Interface

The most important boundary for a software project is its external interface, that which the users directly interact with and which you give backwards compatibility guarantees for. For a web-service, this would be the URL scheme and the shape of JSON request and responses. For a command line application — the set and the meaning of command-line flags. For an OS kernel — the set of syscalls (Linux) or the blessed user-space libraries (Mac). And, for a programming language, this would be the definition of the language itself, its syntax and semantics.

Sometimes, however, it is beneficial to install somewhat artificial, internal boundaries, a sort-of macro level layers pattern. Boundaries have a high cost. They prevent changes. But a skillfully placed internal (or even an artificial external) boundary can also help.

It cuts the system in two, and, if the cut is relatively narrow in comparison to the overall size of the system (hourglass shape), this boundary becomes a great way to understand the system. Understanding just the boundary allows you to imagine how the subsystem beneath it could be implemented. Most of the time, your imaginary version would be pretty close to what actually happens, and this mental map would help you a great deal to peel off the layers of glue code and get a gut feeling for where the core logic is.

Even if an internal boundary starts out in the right place, it, unlike an external one, is ever in danger of being violated. “Internal boundary” is a very non-physical thing, most of the time it’s just informal rules like “module A shall not import module B”. It’s very hard to notice that something is not being done! That’s why, I think, larger companies can benefit from microservices architecture: in theory, if we just solve human coordination problem, a monolith can be architectured just as cleanly, while offering much better performance. In practice, at sufficient scale, maintaining good architecture across teams is hard, and becomes much easier if the intended internal boundaries are reified as processes.

It’s hard enough to protect from accidental breaching of internal boundaries. But there’s a bigger problem: often, internal boundaries stand in the way of user-visible system features, and it takes a lot of authority to protect internal system’s boundary at the cost of not shipping something.

A system boundary is a publicly exposed interface that third-party developers are going to use. A system boundary usually takes the form of a versioned artifact in some fashion. We know it’s inevitable that we’ll have to break things, so we try to only do that with new major versions. With a boundary, we have a responsibility to external users, and versioning puts the onus on us. We can decide if the benefits of a breaking change are large enough to merit having to also maintain another older version.

The primary reason we like boundaries is that they’re the only approach we have to truly re-using code. This is part of the reason we often simulate boundaries even internally to a program.

But while introducing boundaries has its re-use benefits, it also introduces costs. Changes cannot be easily made anymore. Multiple versions may need maintaining. Different dependencies may themselves depend on different versions of the same library, and this imposes costs on anyone who uses a library.

A big part of software design is the design of the abstractions themselves. It’s not just that dependencies have costs, it’s also a major design element. The single most important thing about any module is what modules it does not depend upon. The fewer dependencies it has, the more it can be understood on its own, independently of the rest of the system. It’s sometimes nice to write code in a way that deliberately cuts itself off from the rest of the system, just so it’s clear it’s independent.

## iterative improvement

The best approach we have for doing software development is iterative improvement. We have to start with something and then we can figure out how to make it better.

You can implement concurrency using either threads or processes, where the main difference between the two is that threads share memory and processes don’t. The choice of threads vs. processes comes with various trade-offs and performance implications.

When benchmarking short programs, you often encounter two big problems that mess up your final results: (1) hardware and operating systems are full of side-effects that are neither transparent nor directly manipulable and (2) compilers can optimize in unpredictable ways, requiring IR/Assembly inspection and knowledge of compiler intrinsics.

Ideally, whenever you make a change to the codebase, you want to be confident about which part of the code you need to change, and you want to be confident your change is not going to break the rest of the program.

## Tools

We use a lot of tools for software development. Compilers, linkers, package managers, code linters, and, of course, IDEs are essential parts of our work and life.

Most of the time, an IDE deals with incorrect code. Although we expect IDEs to report errors, their primary goal is not to complain about the inability to do this and that! IDEs drive users to the correct code by staying alive in the presence of errors and suggesting fixes.

Macros take code as an argument and are able to add new code, replace a given code with anything else, or modify this code in any way imaginable. Macros are expanded when our code is compiled. More interestingly, they should also be expanded when we write our code in an IDE. Why? Because an IDE should be aware of expanded code in order to provide us with reasonable navigation and code completion. If a macro fails to expand properly, an IDE is in trouble and its ability to deliver helpful information to a user is severely limited.

# A/B 测试

当没有足够多的信息，在我们不确定什么决策是正确的时候，通常会依赖于直觉做决定。但是直觉并不总是对的，最好的决策需要把直觉、经验和事实综合起来考虑，通过 A/B 测试的流程来知道我们的直觉是否是对的。

A/B 测试是在保持其他变量相同的情况下，比较一两个关键变量引发的结果。A/B 测试过去主要用在市场营销和广告中，现在也是一些精益创业公司快速寻找价值增长的方法。

## A/B 测试的 4 个步骤

1. 获得稳定的数据流：自动采集数据并且提供易用的数据分析工具。
2. 找到对比组：各组拥有近乎相同的特征。
3. 设定测试目标：改变什么变量，然后测量什么指标。
4. 同时进行两种不同的选择，实时地观察相应的结果。

## 软件开发

让自己成为自己开发的产品的第一批用户的实践, 我们称为 dogfooding.

### 需求确认

需求确认的方法：分析、仿真、演示，目的是对需求规格说明中描述的需求的正确性、一致性、完整性、可行性、必要性、可测试性进行确认。

- 分析

通过对需求规格说明的分析来确认软件需求的方式，通常就是审查或评审。虽然全凭想像，但是有客户和开发人员一起分析，应该可以实现确认的目的。

- 仿真

通过使用一种低保真的模型模拟软件的方式来确认需求。由于有了可感知的东西，需求的确认更加可信。

- 演示

当具备了初步的软件原型的时候，就可以通过软件原型的演示对需求进行确认。这这种需求确认的方式可信度最高，因为他和将来软件的使用场景非常接近。

需求确认的内容一般包括以下特征/内容：

1. 正确性

需求描述必须是正确的。否则，实现的软件就是错误的。而需求的正确性只能由客户来确定。但是客户的思维方式和开发人员完全不同，所以，要让客户做好需求正确性的确认，应当尽可能地使用客户的语言描述或解释需求，最好让客户感知到软件的使用场景。

2. 一致性

需求描述的一致性有几个层次。首先是需求规格说明上下文的一致性。比如，对同一术语，上下文要保持一致。其次是与其他软件需求或高层需求一致性。比如，与用户需求的一致性；与非功能需求的一致性。

3. 完整性

完整性也有两个方面的含义。一是需求描述元素的完整性，包括状态，状态变化，转入，产品和约束等。二是需求与客户的期望相比是否有遗漏。这个层次的完整性在确认客户需求的时候就应由客户来做确认，在对需求规格说明进行确认时，也可以再次确认需求的完整性。

4. 可行性

需求必须是可实现的。要综合考虑技术水平、资源保障等多方面的因素。

5. 必要性

客户提出的需求不一定都是必要的。软件开发人员应当从软件帮助客户解决的问题的终极目标出发，考虑技术和环境的限制，分析软件的需求，确定哪些需求是必要的，哪些需求是冗余的。

6. 可测试性

软件的需求一定是可测试的，否则就无法进行验证和确认。需求的可测试性要求需求应当尽量采用量化的描述方式。

## 公司为什么需要建立一套统一的开发框架

1. 避免重复性技术研究——节约人力成本
   让项目组把精力更多的投入到业务中。在项目组之下构建一个基础的开发架构平台，把技术的共性问题提炼出来，交给这样一个团队负责处理。避免每个项目都独自去解决遇到的各种各样的技术难题，有效的把精力释放出来。

2. 标准化技术规范——提升产品项目质量
   采用统一的开发框架（平台）后，在技术栈，技术组件，技术实现方案，甚至在代码规范上就能形成标准化的技术输出模式，标准化带来的最大效果不仅仅开发效率的快速提升，还有产品质量的大幅提升。

3. 进行技术沉淀——提升公司整体技术能力，避免陷入一个人的能力决定一个项目
   技术的进步来源于不断的技术积累和沉淀。每个工程师都是站在别人肩膀上完成工作的。以项目为导向的技术团队，一般都会以实现业务需求为最重要的目标，技术只不过是完成业务的一种工具而已。基于此，业务开发团队就不可能把技术积累作为一项重要的工作。  
   当存在核心同事离职时，平台的研发同事可以对新进入项目的同事进行相关培训，不会导致青黄不接的事情发生。而且，专注于平台的同事为了更好的满足项目组的技术需求，对平台进行不断的改进，从而达到技术积累和沉淀的目标。

4. 可衡量的研发投入——对研发团队的有效管理和考核
   当基于同一开发框架的标准化技术规范建立起来后，对业务功能的代码实现就可以进行相对有效的评估和考量，可以避免因为技术实现差异而出现的种种问题。这对 KPI 的制定和考核是一个巨大的帮助。

### 需求分析

拿到产品需求就开始吭哧吭哧的做方案设计，这是新人通常容易犯的错。有时候产品经理所做的需求方案设计并没有考虑充分。 我接触到的有些产品是直接拿着竞品的特性对着抄的，而且大多数时候是只考虑了正常情况，异常情况并没有考虑进去。又或者本身就不太适合做到现有系统里。导致做完实现后产品可能又说这个需求不做了。网上有很多段子说程序员与产品的有些矛盾就是这么来的。但本身这个事情开发这边也有错。拿到需求后，我们可以遵循如下方法先走一轮：

what【这个需求是什么，在什么场景下使用，谁来用】
why 【为什么要做这个需求？能给用户带来什么价值?】
how 【怎么做，是否可以不做，是否可以换其他方式来达到同样的目的？异常情况有哪些，针对异常情况如何处理？有哪些潜在的体验问题或者性能问题？】
when 【这个需求完成时间结点是什么时候？跟哪个版本？什么时候转测？是否是重点特性？】
跟产品经理谈 what 和 why 以及 how。可以帮助他理清楚需求的细节，把异常情况都考虑进去。 在这个阶段可以把不靠谱的需求 pk 掉或者修改掉。但是这种方式不太适用于老板的需求。如果对方以这是 boss 的需求为由，除非很不靠谱，要不就只能埋头做了。 谈 when 可以帮助你理清楚需求的优先级和重要程度，进而重新调整自己工作任务的优先级。

### 方案设计

- 借助图示剖析系统。人脑能够记住的东西有限，拿到系统之后。把脉络梳理出来。可以借助 processon 在线作图工具，把系统的状态流转图，以及 流程图 画出来。在这些流程过程中需要传递什么数据，需要缓存和持久化什么数据自然就出来了。然后再设计内存数据模型以及持久化数据模型。

- 方案设计先走常规流程，再覆盖异常情况。
  跟人讲设计方案的时候，只讲正常处理流程。这样子方便讲清楚梗概。 然后再讲异常情况，边界情况处理。 作为方案的后续补充。
- 做方案设计永远要准备 B 方案。陈述利弊，调研清楚类似产品的方案实现有缺点。要有推导过程。 没有推导过程的方案难以服众。

- 编程要提炼抽象和重构能力。
  抽象是使得接口简洁，隐藏实现细节，构造可维护可复用代码的一个好的方式。适时的抽象可以减少很多重复无用的工作。

### 统一开发框架的定位和目标

统一开发框架定位于技术层面，其主要目的是为统一公司内相关产品研发和项目实施使用的技术架构和开发工具，有效提高统一技术支持力度，形成持续的技术积累手段，提升技术人员的利用率并降低对人员的依赖性，最终提升软件的规模化、流水线式的生产能力。

### 代码审查

[8 Tips for Great Code Reviews](https://kellysutton.com/2018/10/08/8-tips-for-great-code-reviews.html)

### 敏捷三角：价值，质量和约束。

![](https://insights.thoughtworks.cn/wp-content/uploads/2019/03/AgileTriangle-SWDebt1.png)

传统的项目管理铁三角(范围、时间、和成本)被局部化成一个维度，称为约束。而引入了新的维度，价值和质量。其中价值代表的是利润等正向的因素，而质量代表的是变化的成本。质量越好，意味着变化的成本越低。据此，我们打破铁三角的第一个手段是，关注真正的用户价值，降低变化成本，并为此而调整计划。

持续学习，提升每个个体的效率。我们通常说程序员之间的效率差异会达到数量级的差别。通过自动化减少手工工作，通过预防错误避免返工，改进 DevOps 流程等。

## 测试

大型项目很难通过肉眼检查验证正确性。代码太多，你的大脑很难一次记住。

当测试失败时，仅从测试失败的信息中找到原因也是一个挑战。

从心理学角度来看，在面对一个长年累月的项目时，设置简短的中间态里程碑是很重要的。不断的完成这些里程碑让我干劲十足。

一直让代码保持可编译、可运行和可通过测试的状态也很好。当最终要面对那些日积月累的缺陷时，你将很难下手解决。

## 技术选型

写代码容易，写好很难，每一个部分给出合理设计与实现，并考虑扩展性、易维护、高性能可以说是相当高要求的一件事。

软件设计与实现是需要我们持续投入热情、投入精力的一件事。

对未来以及技术演进方向的把握，可以说是一件非常困难的事情。

每年都会有层出不穷的新技术产生，也会有一些技术走下坡路甚至走向消亡。对于技术发展路径前景需要对当下有深刻认知，以及对未来演进理解才能有一定程度上正确认知，有正确的认知是投资那种技术前提，花费多少时间去学习，能给研发效率带来提升，带来效果提升，以及团队技术水平的提升。新技术能带来一个公司甚至行业巨大发展，判断准确是在技术浪潮之中取得成绩的前提。

新出现的技术如果判断失误，一个小的团队来说就是花费错误的时间与精力去研究没有什么实际价值的技术，花费大量时间成本，对于一个公司判断错误可能就是生死。

减少研发重复性工作投入提升研发效率。以及提升我们实现业务逻辑抽象能力，以及技术研发水平，由研发业务慢慢转移到研发框架。

## 项目规模

一个亿级用户的项目比一个千万级用户的项目的复杂度，不是只高一倍的，项目的复杂度是成指数增长的。你在一个千万级用户项目中遇到的一个小问题，在亿级用户的项目中，却有可能是最难解决的问题。

除了功能需求，还需要考虑安全需求，性能需求，可靠性，稳定性等。这些才是系统设计的难点和关键点。架构师要从产品需求，业务需求里面提出安全，性能，可靠性，稳定性等系统层面的需求。

一个故障发生后，肯定是先处理，然后安抚用户，待一切处理完毕，我们通常会由系统的负责人，出一份故障报告。这份故障报告会详细的记录故障的处理过程，比如 xxx 时 xx 分，xxx 做了什么操作，然后还会详细描述故障产生的原因和后续的改进措施。

这份故障报告写完后，会以邮件的形式发给整个团队，大家会一起来 review 故障的处理过程和故障产生的原因。

我们会定期举行故障复盘会议，大家会在一起讨论问题的根本原因和改进的措施，更进一步的，会由点及面的延展开来，全局看待问题。

有意识地去分享和打造自身的影响力是特别重要的。对外分享，可以是写篇文章，可以是写个 ppt，给组里，给整个项目团队，或者给一些外部会议做分享，都可以慢慢地积累起这种影响力。

### 基本功

什么是基本功？不是那些高大上、新潮的技术、框架，而是程序员每天做的基础工作。比如，快捷键是否熟悉，测试习惯好不好，代码干不干净，打字速度有多快等等。程序员的基本功才是真正影响开发效率，甚至影响整个项目成败的核心。

能做和能做好是两回事。在我看来能做就是程序员懂得这个招式是干什么的，知道做什么，需要用什么招式。而能做好则指的是能够熟练使用招式，运用自如的同时可以举一反三。而能做和能做好之间差的就是基本功。

程序员 80% 的工作，尤其软件开发方面，都是在用基本功，而不是内功。

因为软件开发这个工作，确实大部分的时间，都是在搬运代码和改 bug ，而这些工作恰巧都是需要基本功的。

比如快捷键用得好，就是能够节省时间，提高效率；

比如养成单元测试的习惯，就会减少很多 bug 的出现，既节省了测试的时间，又能节省你改 bug 的时间，单元测试的时间，可能都不及你改 bug 时间的十分之一；

比如养成良好的编码习惯，可以大大提高你代码的阅读效率，在产品更新迭代的过程中，你可以非常快速的完成代码的修改；

比如你打字速度很高，绝对提高了你代码编写的速度；

虽然基本功都是非常常识性的，非常简单的东西，但是就是这些往往看似简单的东西，大家都不重视。这就是典型的还没学会走，就想跑的思想。其实在这个浮躁的社会中，这样的现象太多了，就像练习武术一样，很多武侠人士之所以走火入魔就是不重视练习基本功，感觉这个太简单了，我不想练习，我想直接练大招，学习降龙十八掌。

这样的现象确实很普遍，我所认识的大部分程序员，真的自己写完代码，别说单元测试了，其实自己连简单测试都懒得做。我所经历的公司大部分公司都是不写单元测试的；编码习惯更是各种各样。

所有的事情都是一样的道理：越是简单的东西，大家往往越不重视，而往往越是这些基础的东西才是真正决定能否成功的关键。

基本功就得这样练才行，习惯养成之后，基本功就扎实了，扎实之后，你想不用都难，大脑和肌肉自然而然的就会使出这些基本功。
