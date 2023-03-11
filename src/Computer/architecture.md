# 软件架构

架构就是对系统中的实体以及实体之间的关系所进行的抽象描述，是一系列的决策。

架构是结构和愿景。

画架构图是为了：解决沟通障碍、达成共识、减少歧义。

架构图分为场景视图、逻辑视图、物理视图、处理流程视图和开发视图。

场景视图用于描述系统的参与者与功能用例间的关系，反映系统的最终需求和交互设计，通常由用例图表示。

逻辑视图用于描述系统软件功能拆解后的组件关系，组件约束和边界，反映系统整体组成与系统如何构建的过程，通常由 UML 的组件图和类图来表示。

物理视图用于描述系统软件到物理硬件的映射关系，反映出系统的组件是如何部署到一组计算机节点上，用于指导软件系统的部署实施过程。

处理流程视图用于描述系统软件组件之间的通信时序，数据的输入输出，反映系统的功能流程与数据流程，通常由时序图和流程图表示。

开发视图用于描述系统的模块划分和组成，以及细化到内部包的组成设计，服务于开发人员，反映系统开发实施过程。

以上 5 种架构视图从不同角度表示一个软件系统的不同特征，组合到一起作为架构蓝图描述系统架构。

在画出一个好的架构图之前，首先应该要明确其受众，再想清楚要给他们传递什么信息 ，应该根据受众的不同，传递的信息的不同，画出相应的架构图。

# 架构师的思维模型

## 1、工欲善其事，必先利其器

### 1.1 遍寻天下珍宝

### 1.2 十年磨一剑

## 2、十八般武艺样样精通

### 2.1 不同的项目适用不同的工具

如果一艘快艇足够承载下你的所有货物到达彼岸，那么你不需要使用一艘轮船出行。产品设计和技术选型也是一样，我们不会单纯的说 A 方案比 B 方案好，只是在解决特定的问题上，A 方案比 B 方案更合适，选择了 A 方案的同时也意味着接受 A 方案里那些不如 B 方案的地方。在特定领域问题上的优化和定制方案往往能够取胜于解决更多领域问题的通用方案。

### 2.2 不同人有不同的称手的工具

## 3、常用常新

### 3.1 关注新的动态

### 3.2 适时更新技术体系

# 服务端的架构设计

## 架构设计的核心原则：以简驭繁。

> Write it the right way first time, and make sure you only move on when it's done right.
>
> 垃圾会制造垃圾，一个放在系统里不经清理的额外复杂度，会导致更多的额外复杂度的生成。

## 服务端架构的三个层次

### 一、 数据层：数据库表结构的设计

数据结构的设计是一件严肃的事情，不能随意。数据层是整个架构的最底层，关系着上面各层功能实现的难易程度和运行效率。

数据设计的要点：

- Single Point of Truth，没有冗余数据。
- 反映真实需求，与业务模型中的概念有对应关系。
- 兼具灵活性，做前瞻性的考虑，固化不容易发生改变的规则。

### 二、能力层：功能模块的实现

功能模块的实现需求精心组织，不能临时堆砌。

要点：

- 正交性：同一个功能只有一个实现，没有重复的代码(DRY)。
- 完备性：涵盖增删改查等所有的功能点。
- 组合性：小的功能点可以组合起来实现一个大的功能。

### 三、服务层：微服务的划分

服务层的关键增值是在基础数据之上实施业务约束，资源总是最终要被业务约束才行。微服务是对外提供能力的接口，划分的原则是各微服务之间尽量减少相互调用，不同的微服务组合起来则可以实现完整的业务需求。微服务部署的规模可大可小，满足业务的伸缩性，最大化利用服务器资源。

要点：

- 独立性：微服务能够避免避免单点失败，每一个服务都可以独立开发，测试、部署和更新。
- 正交性：Single Responsbility，专注于单一职责。
- 可复用：同一微服务可在不同的项目之间重复使用。
- 封闭性：构建强相关的方法的小集合，服务内部实现的更新和迭代不影响调用的消费端。
- 提供 RESTful 和 GraphQL 接口

服务接口根据“是否需要即时响应”可分为两种类型：问答型和任务型。问答型由同步的请求/响应模型实现。任务型由事件驱动模型实现，在消息队列里的任务将保持等待状态直到它可以被执行，因而是异步的。

## 业务设计

业务设计是产品设计的重要组成部分，定义各种业务逻辑，由产品经理共同参与完成。对业务逻辑的考量和实现贯穿于服务端的各种层次。

要点：

- 简洁清晰：容易被用户和开发人员理解和执行，不易出错。
- 严密性：考虑各种可能使用场景，不留漏洞。
- 文档化：业务流程有图表和文档记录，设计、开发、测试三方共同使用。

1/3/5 秒原则：在 1s 以内得到响应，用户会觉得系统响应很快，体验非常好；1-3 秒得到响应，用户可以接受，体验还不错；3-5 秒才响应，用户就感觉慢了，体验有点糟糕；一旦响应超过 5 秒，用户就会认为是个失败的体验，选择离开或重新发起请求。

## 用户界面

客户端的实现提供用户交互界面，是影响用户体验的重要因素。

## 数据表设计案例

要做好架构，主要就是要做好抽象，做抽象的方式是类比，做类比的方式可以使用用例图。

例如：![用例图](https://images2018.cnblogs.com/blog/397048/201807/397048-20180712104243712-615972405.png)

好的架构必须需要贴合业务，选择一个投入产出比最优的方案。

降低复杂度、降低理解难度，是实实在在的收益。

## 扩容

1、单体应用
2、反向代理、API 网关
3、负载均衡
4、微服务
5、读写分离
6、消息队列
7、CDN 内容分发
8、分片
9、DNS 域名解析

## [C4 模型](https://c4model.com/)

C4 模型使用容器（应用程序、数据存储、微服务等）、组件和代码来描述一个软件系统的静态结构。

1、语境图 (System Context Diagram)描述自己的系统与用户和周围其它与之相互作用的系统。

2、容器图 (Container Diagram)把语境图里待建设的系统做了一个展开。

3、组件图 (Component Diagram)是把某个容器进行展开，描述其内部的模块。

4、类图 (Code/Class Diagram)描述类或模块的调用关系。

不论是哪种画图方法论，我们回到画图初衷，更好的交流，在画的过程中不必被条条框框所限制。

## 技术架构

架构师也可以分为初级、中级、高级三档，江湖上真正高水平的软件架构师就更少了。

1. 码农分为真的能写代码的，以及自认为能写代码的。

1. 真的能写代码的码农又分为自认为写的不错的，以及真的还不错的。

1. 真的能写不错代码的码农又分为会钻研会不断优化的，以及安于现状的。

1. 会钻研的码农又分为喜欢广度了解新技术蜻蜓点水的，以及深入钻研用到知识的。

1. 了解广度的码农又有少部分愿意深入某些技术，喜欢深入研究的又往往缺乏广度知识。

1. 极少深度广度都关注的码农又分为为技术而技术和为业务而技术的。

1. 纯为技术而技术的码农在国内的软件行业需求太少，且需求的往往不是应用软件领域了。

1. 为业务而技术的深度广度都了解的码农，又需要有良好的沟通能力。

1. 而沟通好的，又有一部分当 PM 去了。

1. 然后剩下的，又有一部分慢慢脱离实际开发（不再做任何实现）或者开始依靠拿各种中间件搭积木来作为“架构”手段。

1. 除去这些，剩下对业务有一定了解，对技术广度上有多种涉猎，深度上对部分技术研究彻底，还有很重要的一点，考虑问题足够细致全面。

1. 细致全面善于沟通，技术上深度广度都没问题， 又喜欢这个工作，还会不时做底层实现，从业务和开发两个角度出发，搭出“架构”来是为了开发效率，为了运行效率，为了开发质量，为了业务灵活和运行稳定，为了维护方便等等这样的人，个人认为可以称为“架构师”。

# 多端架构

- 前台：由各类前台系统组成的前端平台。每个前台系统就是一个用户触点，即企业的最终用户直接使用或交互的系统，是企业与最终用户的交点。例如用户直接使用的网站，手机 App，微信公众号等都属于前台范畴。
- 后台：由后台系统组成的后端平台。每个后台系统一般管理了企业的一类核心资源（数据 \+ 计算），例如财务系统，产品系统，客户管理系统，仓库物流管理系统等，这类系统构成了企业的后台。基础设施和计算平台作为企业的核心计算资源，也属于后台的一部分。

前台和后台就像是两个不同转速的⻮轮，前台由于要快速响应前端用户的需求，讲究的是快速创新迭代，所以要求转速越快越好；⽽后台由于⾯对的是相对稳定的后端资源，⽽且往系统陈旧复杂，甚至还受到法律法规审计等相关合规约束，所以往往是稳定至上，越稳定越好， 转速也自然是越慢越好。

中台就像是在前台与后台之间添加的⼀组 “变速⻮轮”，将前台与后台的速率进行匹配，是前台与后台的桥梁。它为前台而生，易于前台使用，将后台资源顺滑流向用户，响应用户。

**以用户为中心的持续规模化创新**，是中台建设的核心目标。

### 中台是「企业级能力复用平台」

当做中台建设的时候，一定是跳出单条业务线、站在企业整体视角来审视业务全景，寻找可复用的能力进行沉淀，从而希望通过能力的复用一方面消除数据孤岛、业务孤岛，一方面支撑企业级规模化创新，助力企业变革，孕育生态。驱动力是自上而下的，从全局视角出发的，并且需要一定的顶层设计。

企业的能力可能包含多个维度，常见的例如计算能力，技术能力，业务能力，数据能力，AI 能力，运营能力，研发能力…… 其中大部分的能力还可以继续细化和二次展开，从而形成一张多维度的企业能力网。可以说，中台就是企业所有可以被「多前台产品团队」复用能力的载体。

前端指的是网站的表示层以及它与后端数据的交互方式。

后端指的是应用程序的数据处理层。这一层负责与数据库通信，并确定将哪些信息发送到要显示的前端。

# 微服务架构

微服务体系结构由轻量级、松散耦合的服务集合组成。**每个服务都实现了单个业务功能**。理想情况下，这些服务应该是**具有足够的内聚性，可以独立地开发、测试、发布、部署、扩展、集成和维护**。

> 微服务就是一些协同工作的小而自治的服务。 ——Sam Newman

> 微服务架构风格是一种将单个应用程序开发为一组小型服务的方法，每个小服务运行在自己的进程中，并且以轻量级机制（通常是 HTTP REST API）通信。这些服务是围绕业务能力建立的，并且可以由完全自动化的部署机构独立部署。这些服务的集中管理只有最低限度，可以用不同的编程语言编写并使用不同的数据存储技术。 ——  James Lewis and Martin Fowler

微服务自 2014 年 3 月由 Martin Fowler 首次提出。

在传统的软件开发当中，大多数软件都是单体式应用架构。在瞬息万变的商业时代背景下，企业必须学会适应这个时代的不确定性。快速试验、快速迭代、更快地推出新产品以及有效改进当前产品。

而单体应用这种软件架构对于企业来说有一个致命缺点——会致使企业对于市场的响应速度变慢。企业决策者在一年内需要做的决策数量非常有限，由于存在依赖关系，其响应周期往往会变得非常漫长。每当开发或升级产品，都需要在一系列体量庞大的相关服务中同时增加新功能，这就需要所有利益相关方共同努力，以同步方式进行变更。

微服务架构可以让团队裁剪出独立部署的交付物以及可维护的服务。

假设服务边界已经被正确地定义为可独立运行的业务领域，并确保在微服务设计中遵循诸多最佳实践。那么至少会在以下几个方面获得显而易见的好处：

- 复杂性：服务可以更好地分离，每一个服务都足够小，能够完成完整的定义清晰的职责；
- 扩展性：每一个服务可以独立横向扩展以满足业务伸缩性，并减少资源的不必要消耗；
- 灵活性：每一个服务可以独立失败，允许每个团队自主选择最适合他们的技术和基础架构；
- 敏捷性：每一个服务都可以独立开发，测试和部署，并允许团队独立扩展和维护各自的部署服务。

每个微服务是孤立、独立的「模块」，它们共同为更高的逻辑目的服务。微服务之间通过契约彼此沟通，每个服务都负责特定的功能。这使得每个服务都能够保持简单、简洁和可测试性。

在这一基础上微服务架构允许企业更自发地采取更深远的业务决策，因为每个微服务都是独立运作的，而且每一个管理团队可以很好地控制该服务的变更。

## 微服务架构的 6 大特征：

1. 每个服务都是一个轻量级、独立和松散耦合的业务单元。每个服务负责一部分功能或者说业务能力，并且做得很好。职责独立。Small with a single responsibility —— “小到只有单一原则”
   关于微服务有多小有两个标准：第一个标准是如果一个类复杂的超过一个开发人员的理解范围，那么它就太大了，需要被继续拆分。第二个标准是：如果它小到可以随时丢弃并重写，而不是继续维护遗留代码，那么它就足够小。这个标准有个很重要的原则就是 Rewrite over Maintain，即 “重写胜于维护”。

2. 每个服务都有自己的 DevOps 计划（测试、发布、部署、扩展、集成和独立维护）。可以独立部署。自动初始化。隔离失败。
   管理分布式应用的复杂性。对于每个服务，能够采用声明出这些初始化。

3. 每个服务都有自己的代码库，由一个小团队管理和开发（主要是用于敏捷环境中）。一个 “微服务” 应该完全和另外一个服务实现彻底的隔离，从开始的代码库就开始隔离。把公共代码作为 “库” 和 “基础设施即代码” 来对待，就像你代码中用到的开源软件。每个服务都可以为其用例选择最佳的技术栈（无需将整个应用程序绑定在一个框架中）。

4. 每个服务负责持久化自己的数据和保持外部状态（只有当多个服务使用相同的数据时，这种情况才在公共数据层中处理）。尽可能降低耦合，使其自治。隐藏内部实现细节。

5. 高度可观察。基础设施自动化。Status aware and auto-scaling ——“关注状态和自动扩展”
   应用应该是能够感知吞吐量的监控指标来自我进行扩展的，要求基础设施可以及时捕获环境的变化。

6. 统一接口。服务通过使用定义良好的 API（智能端点）和简单协议如基于 HTTP 的 REST 协议（哑管道）相互通信。

### 划分微服务边界的 5 个特征

1. 它不会与其他服务共享数据库表
2. 它拥有最少量的数据库表
3. 它设计为有状态的或无状态的
4. 其数据可用性需求
5. 这是真相的唯一来源

如果两个服务不断地互相调用，那么这已经是一个强烈的耦合信号，他们如果并成一个服务可能更好。如果建立服务的开销超过了让其独立的好处。 在这种情况下不如合并成一个服务。

## 服务网格

2017 年之前所有主流的微服务框架，不管是类库性质的 Finagle、Hystrix，还是框架性质的 Spring Cloud、Dubbo，本质上都归于应用内解决方案，都存在以下三个问题：

- **技术门槛高**：随着微服务实施水平的不断深化，除了基础的服务发现、配置中心和授权管理之外，团队将不可避免的在服务治理层面面临各类新的挑战，包括但不限于分布式跟踪、熔断降级、灰度发布、故障切换等，这对团队提出了非常高的技术要求。

- **代码侵入性强**：主流的微服务框架（比如 Spring Cloud、Dubbo）或多或少都对业务代码有一定的侵入性，框架替换成本高，导致业务团队配合意愿低，微服务落地困难。

- **多语言支持不足**：没有一套统一的、跨语言的微服务技术栈。

2016 年 William Morgan 提出了服务网格（Service Mesh）的概念，Linkerd、Envoy、Istio、NGINX Application Platform、Conduit 等新框架如雨后春笋般不断涌现，Linkerd 和 Envoy 于 2017 年先后加入 CNCF 基金（Cloud Native Computing Foundation），最终促使了一代新贵 Istio 的诞生。2018 年，Istio 将发布 1.0 版本，这也许意味着微服务开始进入 2.0 时代。

> A service mesh is a dedicated infrastructure layer for handling service-to-service communication. Consists of a control plane and data plane (service proxies act as “mesh”). - William Morgan, What’s a Service Mesh? And Why Do I Need One?

服务网格独立于具体的服务而存在，这从根本上解决了老的微服务框架在多语言支持和代码侵入方面存在的问题。并且，由于服务网格的独立性，业务团队不再需要操心服务治理相关的复杂度，全权交给服务网格处理即可。

服务网格独创了边车模式，针对每一个服务实例，服务网格都会在同一主机上一对一并行部署一个边车进程，接管该服务实例所有对外的网络通讯。这样就去除了代理模式下中心化架构的瓶颈。同时，借助于良好的框架封装，运维成本也可以得到有效的控制。

### 微前端

微前端（Micro Frontends）是微服务的衍生物。将微服务理念扩展到前端开发，同时构建多个完全自治、松耦合的 App 模块（服务），其中每个 App 模块只负责特定的 UI 元素和功能。

微前端的核心思想：

- Be Technology Agnostic：每个团队都应该能够选择并升级他们的技术栈，而不必与其他团队协调。自定义元素是隐藏实现细节的好方法，同时为其他人提供公共接口。
- Isolate Team Code：即使所有团队使用相同的框架，也不要共享运行时。构建独立的应用程序。不要依赖共享状态或全局变量。
- Establish Team Prefixes：相互约定命名隔离。为 CSS、浏览器事件、Local Storage 和 Cookies 制定命名空间，以避免冲突，明确其所有权。
- Favor Native Browser Features over Custom APIs：使用浏览器事件进行通信，而不是构建全局的 PubSub 系统。如果确实需要构建跨团队 API，请尽量保持简单。（与框架无关，可使用 CustomEvent）
- Build a Resilient Site：即使 JavaScript 失败或尚未执行，Web 应用程序的功能仍应有效。可以使用通用渲染和渐进增强来提高用户的感知性能。

### The mini web servers architecture

Microservices are nothing more than web servers that offer small REST interfaces. Messages are HTTP requests and responses. Message content is usally JSON documents.

### Service discovery mechanism

Each microservice needs to know the location of other services that it wants to call. The standard solution is a service-discovery mechanism.

To provide service discovery, you need to run a service in your system that keeps a list of all microservices and their locations on the network. Each microservice must query the discovery service to find the services it wants to talk to.

### Load balancing

To scale a given microservice, place an HTTP load balancer in front of a set of microservice instances. You can partially deploy and test new versions of a microservice in production by introducing it into the balance set. The ability to make these kinds of small, low-impact, low-risk production changes is a large part of the attraction of the microservice architecture.

### Take a message focused approach to describing the system

Microservices should communicate with each other using messages. It’s often more useful to think about a microservice system in terms of the messages that pass through the system, rather than the services that respond to them.

- Never expose your underlying implementation choices to other services! Each microservice is allowed to go its own way. It’s an antipattern to seek out common business logic (infrastructure, as always, is a special case) and try to write general modules for multiple microservices to use. Why? Because general code is complex, must deal with edge cases, and is a primary cause of incremental technical debt.
  General business rules and domain models always become “hairy” over time, because the general case isn’t sufficient to handle the complexities of the real world. Better to keep everything separate, in simpler case-specific rules and small models on a per-microservice basis. This keeps your microservices independent and allows developers to work in parallel on simpler code bases.
- Type mismatches should be runtime errors instead of compilation errors. Don't use strict types which means you’re building a distributed monolith.

### Diagrams for microservices

To design a microservice system, start with requirements, express them as messages, and then group the messages into services.

- Microservices are represented by hexagons, a hexagon doesn’t represent a single microservice but means one or more running instances of the same kind of microservice.
- Entities external to the system (such as the web browser) are represented as rectangles.
- Entities internal to the system (the load balancer) are represented as circles.
- Solid lines represent _synchronous_ messages.
- Dotted lines indicate _asynchronous_ message.
- Arrows are directed from the client service toward the listening service.
- Open arrowheads indicate observe but don’t consume messages from the queue.
- Closed arrows indicate message is consumed by the receiver

Understanding the message flows in a system is vital. In particular, all messages have an originating client service and a listening service that receives the message.

Microservice diagrams aren’t intended to be formal specifications—they’re for team communication. It’s therefore acceptable to omit elements for the sake of brevity, even if this creates ambiguity.

### The microservice dependency tree

Microservices are dependent on each other by design. As your system grows over time, the dependency tree of services also grows, both in breadth and depth. Fortunately, experience in the field suggests that breadth grows more quickly than depth. As the tree eventually grows deeper, you’ll run into latency issues.

One way is to merge services so that there’s less need for network traffic. This is a valid performance optimization, especially in mature systems. It’s made much less painful by making sure your infrastructure code is in good shape and abstracting away the networking and service-discovery work from your main microservice business logic.

### The asynchronous message architecture

As an alternative to the point-to-point approach, you have one or more message queues that handle all your messages. Your client services publish messages onto the queue, and your listening services retrieve them. A message queue makes the scatter/gather pattern easy to implement and is much more suited to asynchronous patterns in general.

Using a message queue gives you a lot more flexibility, at the price of increased system complexity. With a queue, at least your services don’t need to know each others’ network locations. They still need to know howto find the queue. You have to use message topics to route messages, and your services need to know about those, too.

Almost universally, production systems are hybrids. Asynchronous message queues allow you to be more fault tolerant and let you distribute work more easily. Adding new services is easy, and you don’t have to worry too much about service discovery. On the other hand, synchronous point-to-point is an absolute must when you need low latency. Also, in the early days of a project, it’s much quicker to get started using point-to-point.

### Microservices are software components

Microservices are incredibly useful as structural units of software. They can be considered fundamental units, much like objects, functions, or processes, because they give us a powerful conceptual model for thinking about system design.

- Encapsulated: Microservices deliver on encapsulation in a very strong way—far stronger than language constructs such as modules and classes. They encapsulate a set of semantically consistent activities and data.
- Reusable: Microservices are inherently reusable, because they’re network services that can be called by anyone.
- Well-defined interfaces: Microservices use messages, and only messages, to communicate with the outside world. These messages can be explicitly listed and their contents constrained as needed.
- Composable: Components can be composed together into more capable components that themselves can be composed into larger systems. Microservices are easily composable because the network flow of messages can be manipulated as desired.

### Monolithic projects vs. microservice projects

The monolithic software architecture creates negative consequences, which many have assumed are fundamental challenges that apply to all software development. Many of the challenges, and many of the supposed solutions to these challenges, arise directly from the engineering effects of monolithic architecture and become moot when you take a different engineering approach.

There are three consequences of the monolith. First, all members of the software development team must carefully coordinate their activities so as not to block each other. There’s one code base. If a single developer breaks the build, then all developers are blocked. The code naturally tends toward deep, multidimensional dependency.

The second consequence of monoliths is that they gather technical debt rapidly. There’s no natural limiting force. A well-structured, properly decoupled, clean, objectoriented initial design is too weak to resist the immediate needs of an entire team working against the clock to deliver today’s features. There are too many ways that one piece of code can invade other pieces of code—too many ways to create dependencies.

Finally, the third consequence of monoliths is that they are all-or-nothing deployments. You have an old version of a monolith running in production, and you have a new version on staging. To upgrade production without impacting the business, you have a very stressful weekend ahead of you.

### How microservices change project management

Microservices are small, and a good practice is to limit them to at most one iteration’s worth of work from one developer. In practice, even more accuracy can be achieved by classifying microservices into, say, three complexity levels, also classifying developers into three experience levels, and matching microservices to developers. For example, a level-1 microservice can be completed by a level-1 developer in one iteration, whereas a level-3 microservice needs a level-3 developer to be completed in one iteration. This approach gives far more accuracy than generic agile story point estimates that ignore variations in developer ability.

Microservice code is disposable. It’s literally throw-away. Any given microservice is one iteration’s worth of work, for one developer. If the microservice was badly written, is underperformant in the chosen language, or isn’t needed anymore because requirements have changed, then it can be decommissioned without much soul searching. This realization has a healthy effect on team dynamics: nobody becomes emotionally attached to their code, nor do they feel possessive of it.

The knowledge that each microservice must live or die on its own merits is a natural limiting function for complexity. Complexity makes you weak. Better to write a new, special-case microservice than extend an existing one.

#### Homogeneous components allow for heterogeneous configuration

You can group microservices into different classes with differing business constraints. Some are mission critical and high load—for example, the checkout microservice on an e-commerce website. Others are core features, but not mission critical. Still others are nice-to-haves, where failure has no immediate impact. Questions: Is it necessary for all of these different kinds of microservices to have the same quality level? Do they all need the same level of unit-test coverage? Does it make sense to expend the same quality control effort uniformly on all microservices? No. There’s no justifiable business case for those views.

You should expend effort where it counts. You should have different levels of unittest coverage for different classes of microservice. Similarly, there are different performance, data-safety, security, and scaling requirements.

A microservice approach doesn’t change the reality that developer resources are limited and ultimately there may not be enough time to build everything. It does let you take a breadth-first approach. With the breadth-first approach, you cover all the cases the business people thought of, at some level. You haven’t wasted effort fully completing features that will turn out to have no value. Microservices make allocation of finite development resources more efficient and friendly.

#### There are different types of code

Microservices allow you to separate business-logic code from infrastructure code. Business-logic code is driven directly from business requirements. It’s determined by the best guesses of the business stakeholders, given incomplete and inadequate business information. It’s naturally subject to rapid change, hidden depths, and obsolescence. Corralling this business-logic code into microservice units is a practical
engineering approach to managing rapid change.

There’s another type of code in the system: infrastructure code. This is where system integration, algorithms, data-structure manipulation, parsing, and utility code happen. This code is less subject to the vagaries of the business world. There’s often a relatively complete technical specification, an API to work against, or specifically limited requirements. This code can safely be kept separate from the business-logic code, so it neither slows down business code nor is negatively impacted by incidental business logic.

The problem with most monolithic architectures is that these two types of code—business-logic and infrastructure—end up mixed together, with predictably negative effects on team velocity and levels of technical debt. Business logic belongs in microservices; infrastructure belongs in software libraries. The ability to allocate coding effort correctly in this way makes estimating the level of effort required for each more accurate, and increases the predictability of the project schedule.
