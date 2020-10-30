### Web Browser

When browsers have first been created, people were very excited. Text and images could be placed and styled with dozens of possibilities. It is a second Gutenberg Revolution, everyone gets access to an infinite amount of information that was previously unreachable. What a great achievement!

Then, those elements became interactive with the addition of a scripting language that can run directly in the browser and modify what is displayed. Suddenly, the browser looks less like a book on a screen and more like newspapers from Harry Potter.

Fast-forward to 2020, browsers are the doorstep to so much more than just animated books. Everyone uses them for everything. Be it watching videos of cute cats or managing stock portfolios. It all happens in the browser nowadays.

A huge number of libraries and frameworks in JavaScript land have tried to make programming more accessible and simple. Their combined power is really what defined modern life in JavaScript land.

### Event Loop

The land of JavaScript is ruled by a thing called the event loop, which schedules different tasks (threads) to run orderly. It defines several rules that all code living in the browser has to obey. For simple JavaScript programming, it is usually okay not to worry about them. But then there are also quite basic cases in which it matters a lot.

Rule number one of the event loop.
> Once a thread is running, it runs to completion without interruptions of other threads.

When the result of some code depends on the order in which the threads access the same data, we call that a race condition. Sometimes, this is intended and perfectly fine. But in other cases, the programmer does not even know that there is a race condition, hence not all possible outcomes will be accounted for. In that case, race conditions are bad.

There are different solutions to avoid the risk of race conditions. The founders of JavaScript thought about this carefully. They came to a drastic conclusion and decided that no concurrency between threads is allowed, for the safety of everybody.

This resolves the race conditions by removing the possibility that multiple threads ever run at the same time. However, the existence of multiple threads should still be allowed, or otherwise, it would be very annoying to write code. So they came up with the event loop, which sequentially runs one thread after another without interleaving them.

### Rust

The founders of Rust are very smart people and they discovered a different approach to solve the issue of race conditions. Instead of forbidding multiple-threads, they forbid sharing mutable data.

Immutable data can be shared, no problem. Mutable data can also be passed from one point to the other. But mutable data sharing from two different locations at the same time is strictly prohibited and will be prosecuted with hefty compiler errors.

This can be formulated as the number one rule of Rust.
> Each variable can have either multiple readers or a single writer. (MRSW)

