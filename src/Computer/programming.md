# Programming

> Everyone in this country should learn to program a computer, because it teaches you to think. — Steve Jobs

> Software is a great combination between artistry and engineering. — Bill Gates

Programming is not merely about language syntax and semantics, but more fundamentally about the iterative process of refining mental representations of computational problems and solutions and expressing those representations as code.

> Programming is about solving technical problems, but how you solve them, and how you think about them is important too, and it's one of those things you start to recognize over time: certain people have that "good taste" thing and pick the "right" solution.
> I don't want to claim that programming is an art, because it really is mostly just about 'good engineering'. I'm a big believer in Thomas Edison's 'one percent inspiration and ninety-nine percent perspiration' mantra: it's almost all about the little details and the everyday grunt-work. But there is that occasional 'inspiration' part, that 'good taste' thing that is about more than just solving some problem - solving it cleanly and nicely and yes, even beautifully.
> I think one of the big successes of Linux is having literally hundreds of maintainers around, all with that hard-to-define "good taste", and all people who maintain parts of the kernel.
> -- Linus

> "Recursion! The cause of, and solution to, all of life's problems!"

> There's a big difference between solving a problem and making a problem go away.

> If you want everything to be familiar, you'll never learn anything new. - Rich Hickey

> There's no such thing as a perfectly intuitive programming language because algorithmic thinking isn't something that comes to us intuitively. That's why the first language is always the hardest.

> Relying on the programmer to always read, comprehend, and remember the documentation – and then do everything right, every time – is how we get bugs.

> “Indeed, the ratio of time spent reading versus writing is well over 10 to 1. We are constantly reading old code as part of the effort to write new code. …[Therefore,] making it easy to read makes it easier to write.”>
> Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship

"Mechanical Sympathy" comes from the great racing driver Jackie Stewart, who was a 3 times world Formula 1 champion. He believed the best drivers had enough understanding of how a machine worked so they could work in harmony with it.

Why does the software we use today not feel any faster than the DOS based applications we used 20 years ago??? It does not have to be this way. As a software developer I want to try and produce software which does justice to the wonderful achievements of our hardware friends.

Coding is to programming what typing is to writing.
Writing is something that involves mental effort you're thinking about what you're going to say.
In the same way, programs are built on ideas, they have to do something and what they're supposed to do is liking what writing is supposed to convey.

If people are trying to learn programming by being taught to code, well they are being taught writing by being taught how to type and that dosn't make much sense.

When you write an algorithm you need to have a proof that it's correct, if you are proving things that means mathematics.

Thinking what program is supposed to do mathematically, write down the ideas that go into the program before you do any coding.

I find that the best way to describe a solution is often to just write the snippet of code - maybe not the whole thing - and just make it very concrete that way.

Programming is a tool to solve problems that you have in the domain of computers.

The purpose of a program is, and ought to be, something that transforms data into other forms of data.

A Value is a datum with an associated type.

A (Data) Type is an attribute of a value which encodes information about how the data value can be operated upon.

An Object is a value with associated behaviour, and thus implies it has agency.

Most programming languages are partly a way of expressing things in terms of other things and partly a basic set of given things.

## PL paradigms throughout history

• 1975: rise of systems languages
-- Efficiency first: we don’t have enough resources, carefully build a system

• 1995: rise of scripting languages
-- Productivity first: systems languages are too hard (and we have the resources), so quickly glue together a system

• 2015: rise of functional languages
-- Correctness first: scripting languages are too buggy, we need to know if our system works

When you’re a beginner, it feels important to invest your time into the “correct” language–lest it all be wasted. To avoid sitting with that discomfort, new programmers often tell themselves that their language or tool is perfect and infallible and lash out at anyone who criticizes it.

## Simple, correct, fast: in that order

The single most important quality in a piece of software is simplicity. The reason is straightforward: if your solution is not simple, it will not be correct or fast.

Given enough time, you’ll find that all software which solves sufficiently complex problems is going to (1) have bugs and (2) have performance problems.

Software is a living thing! The complex problem comes later, and it’ll be better served by the composition of simple solutions than with the application of a complex solution.

When we look at all the stuff we’ve built, it’s easy to forget how we got there: incrementally and painfully.
Sometimes “thinking big” means getting nowhere, fallen into the trap of thinking too big, doing too much, everything seems impossible.

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

N✕M is bigger than N+M, and so we design for composability and orthogonality.

### DRY

DRY is an acronym that stands for “Don’t Repeat Yourself.” If you are doing the same thing in multiple places, consolidate the duplicate code. If you see patterns in your code, that is an indication it is prime for DRYing.

Clean code is a consistent style of programming that makes your code easier to write, read, and maintain.

You aren’t done just because your code “works”. Clean it up by removing dead code (zombie code), refactoring, and removing any commented-out code! Strive for maintainability. Ask yourself, “Will someone else be able to understand this code six months from now?”

A good developer, when faced with a situation where they have to do something more than once, will generally find an automated (or better) solution to complete the task at hand. Because you’re lazy, subscribing to clean-code techniques will decrease the frequency of changes from pull-request code reviews and the need to come back to the same piece of code over and over.

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

### API

Programming involves using and creating APIs. When we're creating a new API, we typically think in terms of defining functions to allow users to work with our library.
A different perspective is to think of these APIs as little languages, or domain-specific languages.

Make your APIs exactly match the structure of the problem.

### Learning

Personally, I cannot learn a new language from simply watching youtube videos, but rather through seeking out solutions for myself, making mistakes, and feeling humbled by the process.

### Pure and Dirty Functions

Functions that always produce the same result given the same input and have no side effects are called pure functions.

Computational effect can be mapped to monads. Monads let us model all kinds of effects using only pure functions.

As a developer, we always like to choose the best thing among several choices available.

The code editor is an application that enables the programmer to write and manipulate the source code.

IDE stands for Integrated Development Environment. It is a Graphical User Interface (GUI) based software which allows the programmers to write, debug, release, and deploy their code.

Syntax highlighting means that the editor displays the text, more specifically, the source code in different colors according to the programming language being used.

Debugging is the process of finding and removing bugs from a program.

## Data Structures are key to a good program

> Data dominates. If you’ve chosen the right data structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming. -- Rob Pike 1989

> I’m a huge proponent of designing your code around the data, rather than the other way around, and I think it’s one of the reasons git has been fairly successful… I will, in fact, claim that the difference between a bad programmer and a good one is whether he considers his code or his data structures more important. Bad programmers worry about the code. Good programmers worry about data structures and their relationships. -- Linus Torvalds 2006

Good data structures makes coding easy to design and maintain, whereas the best code in the world cannot make up for poor data structures.

RECOMMENDATIONS
R1. Never use global variables
R2. Declare single-purpose variables
R3. Declare variables close to their use
R4. Keep code blocks small
R5. Use variables close to their declaration
R6. Use no more than two nesting levels

REPL: read-eval-print loop

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

#### C Programming Language

Language theorists can occasionally refer to C as a “big macro assembler”, the only thing abstracted away is really the raw instruction set.

C provided freedom, where high-level languages were considered as straight-jackets enforcing unwanted discipline. It was an invitation to use tricks which had been necessary to achieve efficiency in the early days of computers.

We can see why an efficiency-oriented operating system kernel such as Linux will tend toward C.

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

### Naming things

> “There are only two hard things in Computer Science: cache invalidation and naming things.”
>
> – Popularly attributed to Phil Karlton

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

## Error Handling
Things are always going wrong, as I’m sure you’ve noticed, and that applies to our programs too.
An Option type indicates that there may or may not be an answer. 
A Result can be one of two possible variants. It can be either Ok(x), meaning “the answer is x”, or it can be Err(e), meaning “couldn’t get the answer because error e happened”.

## Testing

It’s worse to have bad mocks than no mocks, because they give you a wrong feeling of confidence in your tests—especially when mocks increase test coverage.
Mocking adds complexity, is hard to maintain, introduces its own bugs, doesn't test what should be tested and creates a false sense of security.
Especially when mocking services from other teams. Just had the case and bugs just showed up in e2e test by a qa team.

There are several things you can do instead of mocking:

- More unit testing
- Easier to Test IO
- Just do IO
- Separation of logic and services / IO
- E2E integration tests

### Articles

- [The Art of Separating Actions and Calculations](https://rusty-ferris.pages.dev/blog/fp-actions-vs-calculations/)

### People

SQLite’s author D. Richard Hipp (DRH) did not find existing version control systems suitable. So he wrote his own called Fossil. Fossil is powered by SQLite, of course. This reminds me of how Linus wrote Git. DRH also wrote his own parser generator called Lemon.