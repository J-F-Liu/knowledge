> 要么是用户控制程序，要么是程序控制用户。
> -- 理查德・斯托曼

> Programming is about solving technical problems, but how you solve them, and how you think about them is important too, and it's one of those things you start to recognize over time: certain people have that "good taste" thing and pick the "right" solution.
> I don't want to claim that programming is an art, because it really is mostly just about 'good engineering'. I'm a big believer in Thomas Edison's 'one percent inspiration and ninety-nine percent perspiration' mantra: it's almost all about the little details and the everyday grunt-work. But there is that occasional 'inspiration' part, that 'good taste' thing that is about more than just solving some problem - solving it cleanly and nicely and yes, even beautifully.
> I think one of the big successes of Linux is having literally hundreds of maintainers around, all with that hard-to-define "good taste", and all people who maintain parts of the kernel.
> -- Linus

I find that the best way to describe a solution is often to just write the snippet of code - maybe not the whole thing - and just make it very concrete that way.

Programming is a tool to solve problems that you have in the domain of computers.

The purpose of a program is, and ought to be, something that transforms data into other forms of data.

A Value is a datum with an associated type.

A (Data) Type is an attribute of a value which encodes information about how the data value can be operated upon.

An Object is a value with associated behaviour, and thus implies it has agency.

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

Starting a new project is exciting. You get to try the new database, the new framework, the new architecture, the new everything.
But every new tool introduces a risk. And those risks compound. That’s why I believe that you should choose boring technology for most of your stack and only allow a meagre novelty budget.

There are many stories of applications that are now impossible to maintain because someone decided that the latest NoSQL database, framework, or language would be perfect for the new project. That person has now left and no one knows how to keep the application alive. Luckily, Rust is a programming language for the next 40 years.

The database / business logic split, which is arguably the most successful example of process separation. In this model, the database is responsible for performance and integrity, and the business logic is in a separate process, so it can safely do things like crash and hang.

## Language wars

As an aside, thinking of languages as platforms also explains language flame wars.

Your productivity in any language is directly proportional to your time and effort investment in it. It’s in your best interests to pick the language that’s likely to thrive and spend time learning it’s ins and outs. On the flip side, betting on a horse that doesn’t win could mean the loss of months or years of effort. This is why people evangelize the platforms they’re invested in - convincing other people to join improves the health of the platform, increasing their return on investment.

This evangelizing can sometimes become contentious if others perceive it as an attack on their platform. People defend their language mostly because they don’t want to see it lose popularity. If it did, their language’s viability is threatened and their investment is in jeopardy. It’s also partly because they’ve spent so long on it that it’s become a part of their identity.

That’s something for us to keep in mind as we advocate for a language we like.

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
