# Game

## Main Loop

###### Present, accept, interpret, calculate, repeat

The goal of every video game is to **present** the user(s) with a situation, **accept** their input, **interpret** those signals into actions, and **calculate** a new situation resulting from those acts. Games are constantly looping through these stages, over and over, until some end condition occurs (such as winning, losing, or exiting to go to bed). Not surprisingly, this pattern corresponds to how a game engine is programmed.

The specifics depend on the game.

Some games drive this cycle by user input. Imagine that you are developing a "find the differences between these two similar pictures"-type game. These games present two images to the user; they accept their click (or touch); they interpret the input as a success, failure, pause, menu interaction, etc.; finally, they calculate an updated scene resulting from that input. The game loop is advanced by the user's input and sleeps until they provide it. This is more of a turn-based approach that doesn't demand a constant update every frame, only when the player reacts.

Other games demand control over each of the smallest possible individual timeslices. The same principles as above apply with a slight twist: each frame of animation progresses the cycle and any change in user input is caught at the first available turn. This once-per-frame model is implemented in something called a **main loop**. If your game loops based on time then this will be its authority that your simulations will adhere to.

But it might not need per-frame control. Your game loop might be similar to the find the differences example and base itself on input events. It might require both input and simulated time. It might even loop based on something else entirely.

## Game Engine

Unity3D is a development engine that was first released in 2005. Since then it’s become the most popular 3D and 2D development platform in the world.

Unity is good for both cross platform solutions and complex XR projects alike.

Unreal Engine has a long history as a game engine dating back to 1998. Over its lifespan it was licensed to a handful of AAA-studios for titles like Duke Nukem and Deux Ex. It’s had several iterations, such as Unreal Engine 2 & 3. Things took a U-turn in 2015, when the 4th version of this ubiquitous development engine was made free to the general public.

Unreal Engine 4 can be used for VR/AR development, 2D, 3D and mobile development alike.

Both Unreal Engine 4 and Unity3D are capable of creating photo-realistic scenes and provide tools for creating stunning visuals.

Unity3D, as a freely accessible engine, has been around longer than Unreal Engine 4, so, naturally, it has a bigger community of indie developers surrounding it.

Unreal Engine 4 is an open source engine, you can modify UE4 source code to fit your needs, free of charge. Unity3D is not, you can view Unity3D source code, but in order to modify it you need to acquire enterprise license. If you need some custom functionality in Unity3D, in most of the cases platform-based scripting and plugins from the asset store should be enough.

Unreal Engine 4’s community is divided between non-programmers who create application mostly with visual scripting system called Blueprints and developers who know and use C++.

On the contrary, every Unity3D developer knows C# — its primary development language, so that experienced developers can easily show beginner developers the ropes.

Due to the advances of XR technology, businesses, education centers, and manufacturing enterprises are extensively using XR applications to improve their workflow and profits in a myriad of ways.

#### Assets Store

Every virtual environment has to be populated with virtual objects that represent a real or imaginary world.

You can create 3D assets from scratch using a 3D modeling software such as Maya, Blender or 3ds Max, or you can purchase the assets via the Assets Store.

Both Unity and Unreal Engine have assets markets that allow you to purchase pre-made 3D models, objects, environments and so on.

### Chess

♔ White Chess King
♕ White Chess Queen
♖ White Chess Rook
♗ White Chess Bishop
♘ White Chess Knight
♙ White Chess Pawn

♚ Black Chess King
♛ Black Chess Queen
♜ Black Chess Rook
♝ Black Chess Bishop
♞ Black Chess Knight
♟ Black Chess Pawn

红方 黑方 字母 相当于国际象棋中的棋子 数字 英文
帅 将 K King(王) 1 General
仕 士 A Advisor(没有可比较的棋子) 2 Advisor
相 象 B Bishop(象) 3 Elephant
马 马 N Knight(马) 4 Horse
车 车 R Rook(车) 5 Chariot
炮 炮 C Cannon(没有可比较的棋子) 6 Cannon
兵 卒 P Pawn(兵) 7 Soldier

亚洲规则与中国规则的区别主要在于循环招法出现时的判罚不一样。对于“长打”的定义，中国规则和亚洲规则不完全一样，以下几种“长打”在国内规则中是禁止着法，而在亚洲规则中却是允许着法：A. 长要杀；B.长要抽吃；C. 多子长捉一真根子；D. 一将一捉；E. 分捉多子。
比如一将一捉在中国规则是不允许的，在亚洲规则允许。按照中国规则，二打对二闲，黑方变着，不变作负。若按照亚洲规则，一照（将）一杀，双方不变作和。

中国规则的原则性比亚洲规则强，更为严格，只要打的过程中存在得利的行为，例如要杀、要抽吃、多子捉一真根子，长打就算禁止着法。但是，亚洲规则的判断方法比中国规则简单，在没有裁判的网络对局中，计算机可以判断将、捉等直接攻击的着法，而对于要杀、要抽吃等间接攻击，计算机很难作出判断，因此在可行性上讲，亚洲规则比中国规则更合理，所以软件通用的是亚洲规则。

2017 年 11 月在菲律宾举行的象棋世锦赛期间，为了顺应象棋发展的时代潮流和最新需求，世象联第七届执委会第一次会议形成决议，在亚洲《象棋比赛规例》第四次修订本的基础上制定、编辑、出版统一的《世界象棋规则》。在亚洲象棋联合会的支持下，世界象棋联合会与中国象棋协会审定后，以第四次修订的“亚洲象棋比赛规例”为基础的“世界象棋规则”正式对外公布，第一次以中、英双语发行的“世界象棋规则”，原则没动，只对结构进行了一些修订、调整。
