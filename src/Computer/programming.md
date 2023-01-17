# 程序设计

> 要么是用户控制程序，要么是程序控制用户。
> -- 理查德・斯托曼

> 最好的程序员不是善于编写复杂代码，而是有能力为复杂的问题提出简单的解决方案。只有糟糕的程序员，才会对简单的问题提出复杂的解决方案。

> "减少人类的苦难"，对我来说就是软件价值的核心。我过去和现在所做的工作都以此为目标。

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

## Tools

We use a lot of tools for software development. Compilers, linkers, package managers, code linters, and, of course, IDEs are essential parts of our work and life.

Most of the time, an IDE deals with incorrect code. Although we expect IDEs to report errors, their primary goal is not to complain about the inability to do this and that! IDEs drive users to the correct code by staying alive in the presence of errors and suggesting fixes.

Macros take code as an argument and are able to add new code, replace a given code with anything else, or modify this code in any way imaginable. Macros are expanded when our code is compiled. More interestingly, they should also be expanded when we write our code in an IDE. Why? Because an IDE should be aware of expanded code in order to provide us with reasonable navigation and code completion. If a macro fails to expand properly, an IDE is in trouble and its ability to deliver helpful information to a user is severely limited.
