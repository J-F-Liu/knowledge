Parsing is a process of deriving structure from a stream of data. A parser is something which teases out that structure.

I spent over 20 years assuming that parsing is easy and that I didn’t need to understand it properly in order to use it well.
Alas, reality has been a cruel teacher, and in this post I want to share some of the lessons I’ve been forced to slowly learn and acknowledge.

### Recursive descent parser

one writes a series of functions which examine the input string at a given position and, if they match at that position, advance the parse.
the “obvious” way of implementing left associativity in a recursive descent parser causes an infinite loop.

Over time, I’ve come to view recursive descent as the parsing equivalent of assembly programming: maximum flexibility, maximum performance, and maximum danger.

### Generalised parser

They can parse any CFG, it is possible for such parsers to return all the ambiguous possibilities, but that’s not very useful for programming languages.
We expect compilers to settle on a single meaning for the programs we throw at them.

Over time, I’ve come to view generalised parsing as equivalent to dynamic typing: expressive and safe, but with more errors than necessary being deferred to run-time.

### LL and LR parsing

In essence, these approaches describe subsets of the CFGs which provably contain only unambiguous grammars.

LL grammars naturally map to recursive descent parsers (but not necessarily vice versa).

To my mind, the combination of LL and recursive descent parser has a small but important niche: if you really, truly need the highest possible performance and/or you want the best possible error messages, this is probably the best route we know of. However, it comes at a significant cost.

LR is strictly more powerful than LL, LR grammars are the largest practical subset of unambiguous CFGs that we currently know how to statically define.
LR parsing works by generating a statetable at compile-time that is then interpreted at run-time.

Over time, I’ve come to view LR parsing as equivalent to static typing: occasionally annoyingly restrictive, but providing enough static guarantees to be worth the annoyance for important software.

Challenges:
- Design error resilient (and not just error recovering) LR parsing algorithm.
- Incorporate precedence and associativity tables into the surface syntax of the grammar.
- Implement LSP server which provides basic IDE features, as well as live preview.

### Pratt Parsing

Pratt Parser is a top-down operator-precedence (TDOP) recursive descent parser.
[Original paper](https://tdop.github.io/)
[Tutorial](https://eli.thegreenplace.net/2010/01/02/top-down-operator-precedence-parsing)