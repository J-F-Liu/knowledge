
Anyone trying to make a new mainstream language is completely insane, unless they're backed by a large corporation.
There are only two exceptions in the last 25 years that come close: Scala and Kotlin. They did this by seamlessly building on an existing ecosystem, specifically Java's.

Anyone who has tried to make Java call C, or Python call Javascript, or C call Rust, can tell you that it's really difficult to call functions from other languages.
Heroes throughout the ages have created tools like SWIG, CXX, etc. which at least make it possible for a user to reach across the Foreign Function Interface (FFI) boundary, if they can figure out the correct incantations.
But even with these tools, it's so difficult that we often just give up and call a microservice instead.

And unfortunately, seamlessly building on Rust's ecosystem is impossible...
Calling into Rust is even harder; you can't just slap an extern onto your function, because Rust doesn't have a stable ABI; rustc-compiled functions don't have a predictable signature that the linker can recognize.
MIR is rustc's "Mid-level Intermediate Representation". rustc turns Rust source code into HIR, then MIR, then eventually, LLVM IR, which later gets turned into assembly code.

If you’re designing a language from scratch, trying to create syntax for your language without first knowing its semantics is a trap.
The goal of writing a parser is to produce an AST. But we don’t have to parse our AST out of text during prototyping, we can design an AST and then construct it ad hoc where we need it.

### Starting with types
Types are the central organizing principle of the theory of programming languages. Language features are the manifestations of type structure. 
The syntax of a language is governed by the constructs that define its types, and its semantics is determined by the interactions among those constructs.

## 数据类型

Imperative programming involves code operating over a world of objects, these objects have types, which enumerate the set of possible values the object could have, and these objects exist at places; as a result they also have a notion of identity, in that while two different objects at different places may have the same value, they do not have the same identity.
In Rust places are mutable or immutable. They can also be moved, so that they are no longer valid for any operation. 
An object at a pinned place cannot be moved from and cannot be borrowed with the &mut operator. However, it can be assigned to (if it is also mutable) and it can be borrowed with the & operator. 

Data types:

- Number: integer, rational, complex, quaternion
- String
- Tuple
- List
- Dict
- Set
- Function

|   类型   | 语法             | 描述                                       |
| :------: | ---------------- | ------------------------------------------ |
|   nil    | nil              | 表示一个空值（在条件表达式中相当于 false） |
|   bool   | false, true      | 布尔类型，包含两个值：false 和 true        |
| integer  | 123              | 整数，不限精度                             |
|  float   | 1.23             | 双精度浮点数                               |
| rational | 3/7              | 由两个整数构成的有理数                     |
| complex  | 2+3i             | 由两个浮点数构成的复数                     |
|  string  | "abc"            | 字符串                                     |
| function | fun(){}          | 函数                                       |
| closure  | ()=>{}           | 闭包                                       |
|   list   | [1,2,3]          | 数列                                       |
|  tuple   | (1,2,3)          | 元组                                       |
|   dict   | {a: 1, b: 2}     | 字典                                       |
|  range   | 1.\.5            | 区间                                       |
|  regex   | /ab+c?/          | 正则表达式                                 |
| datetime | 2018-04-02T15:12 | 日期时间                                   |

```
fun dot(v1, v2)
  v1.x * v2.x + v1.y * v2.y
end

typ Vec2(x,y)

var a = Vec2(2, 3)
let p = dot(a, a)

typ Matrix[[]]
typ Person{name: String, age: Integer, gender: Enum}
```

```
line comment --
block comment =- ... -=
symbol #sym, #"text", #6c7fe2
char 'c'
string "str", `path`, <<END
multi line
END
string interpolation "hell $who, ${Time.now}"
list [a, b, c]
map { "k": v, #sym: val, $var: value}
if condition then
  code
end
while condition do
  code
end
for item in list
  code
end
```

语句以换行结尾。
如果一条语句分多行写，断句处要求最后一行前面的几行合起来是不完整的，简单的做法是给最长的表达式加括号。

let res = perform_action()? 有可能出错并返回错误值
let res = perform_action()! 异步执行

Types are values that must be known at compile-time.
A generic data structure is simply a function that returns a type.
Compile-time reflection and compile-time code execution.

```zig
const std = @import("std");

const Header = struct {
    magic: u32,
    name: []const u8,
};

fn printInfoAboutStruct(comptime T: type) void {
    const info = @typeInfo(T);
    inline for (info.Struct.fields) |field| {
        std.debug.print(
            "{s} has a field called {s} with type {s}\n",
            .{
                @typeName(T),
                field.name,
                @typeName(field.field_type),
            },
        );
    }
}

fn List(comptime T: type) type {
    return struct {
        items: []T,
        len: usize,
    };
}

pub fn main() void {
    var buffer: [10]i32 = undefined;
    var list = List(i32){
        .items = &buffer,
        .len = 0,
    };

    std.debug.print("{d}\n", .{list.items.len});
}
```

Rust has patterns, traits, dyn, modules, declarative macros, procedural macros, derive, associated types, annotations, cfg, cargo features, turbofish, autoderefencing, deref coercion etc.
Zig manages to provide many of the same features with a single mechanism - compile-time execution of regular zig code.

When writing a generic function, rust will prove that the function is type-safe for every possible value of the generic parameters. Zig will prove that the function is type-safe only for each parameter that you actually call the function with.
This allows zig to make use of arbitrary compile-time logic where rust has to restrict itself to structured systems (traits etc) about which it can form general proofs. This in turn allows zig a great deal of expressive power and also massively simplifies the language.
On the other hand, we can't type-check zig libraries which contain generics. We can only type-check specific uses of those libraries. This means zig also doesn't get the automatic, machine-checked documentation of type constraints that rust benefits from and may face more challenges providing IDE support.

```zig
// This function is typesafe if there exist no odd perfect numbers
// https://en.wikipedia.org/wiki/Perfect_number#Odd_perfect_numbers
fn foo(comptime n: comptime_int, i: usize) usize {
  const j = if (comptime is_odd_perfect_number(n)) "surprise!" else 1;
  return i + j;
}
```

In rust, you can use `#[derive(Ord)]` to create a default implementation of the Ord trait for a type. If you don't do this, users of your library cannot do it themselves because of the orphan impl rules. If you do do this, users of your library pay for the extra compile time even if they never use it.

The equivalent in zig looks like this:

```zig
pub fn compare(a: anytype, b: @TypeOf(a)) Ordering {
    const T = @TypeOf(a);
    if (std.meta.trait.hasFn("compare")(T)) {
        // if T has a custom implementation of compare, use that
        return T.compare(a, b);
    } else {
        // otherwise, use reflection to derive a default implementation
        switch (@typeInfo(T)) {
           ...
        }
    }
}
```

This function works on any type, even those from other packages, can be overridden on a type-by-type basis and will only be compiled for functions on which it is actually used. With a little extra work it can also be made extensible by third-party libraries which didn't create the original type.

C++ ABI is not stable across compilers, you must use the same C++ compiler to compile all your objects and static libraries.

## Memeroy Access

Essentially all program state is semantically in memory.
Variables are semantically unaliased until you actually take a reference to them!

- memory is anonymous if the programmer cannot refer to it by name or pointer.
- memory is unaliased if there is currently only one way to refer to it.

It’s fine to make as many copies as you want of readonly pointers, but if you want to actually write to memory it’s really important to know how it’s aliased!

Aliasing rules are some of the most foundational parts of a language’s semantics and optimizations.
Putting something in a register is caching it. If a compiler can’t decide it’s ok to put values in general purpose registers or spill them to the stack, it’s an assembler at best.

Allocations abstractly describe things like individual variables and heap allocations. A freshly created allocation (variable decl, malloc) is always brought into the world unaliased and therefore acts like a sandbox with One True Name. The process of tracking this “chain of custody” from the One True Name to all of its derived pointers is Pointer Provenance.

From a formal memory model perspective, all accesses to an allocation must have provenance tracking back to that allocation. If pointer provenance isn’t satisfied, then that means the programmer broke out of the sandbox or pulled a pointer from the aether that happened to point into some random sandbox. Either way, everything is chaos and nothing makes sense anymore if that’s allowed.

From a compiler optimization perspective, tracking provenance allows the compiler to prove that two accesses don’t alias. If two pointers are known to have different provenance, then they cannot possibly alias and you can get Good Codegen. If it ever loses track of a pointer to some memory (i.e. if pointers are passed to an opaque function) then it has put that memory/pointer in a “may be aliased” bucket. Accesses through two may-be-aliased sources have to conservatively be assumed to alias and can get Bad Codegen.

Type systems are useful not just for the safety guarantees they provide, but also for helping compilers generate more efficient code by simplifying important program analyses.

### CHERI (Capability Hardware Enhanced RISC Instructions)

In CHERI-based CPU, every pointer is tagged with extra metadata that the hardware maintains and validates. If you ever break out of your sandbox the hardware will catch it and the OS will presumably kill your process.

Each pointer contains a compressed slice (range of memory) that it is allowed to point into as well as the actual address that it points to. The slice is that pointer’s sandbox, and all pointers derived from it inherit that sandbox (or less). Whenever you access some memory, the hardware just checks that the pointer is still inside its sandbox.

This metadata isn’t cheap: pointers in CHERI are 128-bits wide, but the effective address space is still at most 64-bit.

In ECC(Error Correction Code) RAM, each RAM stick actually has more physically memory than it claims, because it’s transparently using that extra memory to correct or detect random bitflips.

CHERI has an extra 129th bit which the hardware is hiding from you is a “metadata is valid” bit. You see, to properly manipulate pointers in CHERI you need to access the memory/registers containing a pointer with specific instructions for that task. If you try to manipulate them some other way (say by memcpying random bytes over it), the hardware will disable the “metadata is valid” bit. Then if you try to use it as a pointer, the hardware will see your metadata can’t be trusted and fault/kill your process.

Promoting an integer to a pointer (or what CHERI calls a capability) requires adding metadata to it. What metadata? What range is this random address possibly valid for? There is literally no way to answer that question!

### Distinguish Pointers And Addresses

- Define a distinction between a pointer and an address
- Redefine usizes as address-sized, which is <= pointer-sized (and usually ==)
- Define `ptr.addr() -> usize` and `ptr.with_addr(usize)` -> ptr methods
- Deprecate usize as ptr and ptr as usize

A usize is large enough to contain all addresses for all address spaces on that platform.
All casts from raw pointers to/from integers are to be deprecated.

A pointer points into a specific address space. A pointer semantically has 3 pieces of information associated with it:

- Segment: The address-space it is part of.
- Provenance: An allocation (slice) that it is allowed to access.
- Address: The actual address it points at.

The compiler and hardware need to properly understand all 3 of these values at all times to properly execute your code.

Segment and Provenance are implicitly defined by _how_ a pointer is
constructed and generally propagates verbatim to all derived pointers.
It is therefore _impossible_ to convert an address into a pointer
on its own, because there is no way to know what its segment and
provenance should be.

By introducing a "representative" pointer into the process we can
properly construct a new pointer with _its_ segment and provenance,
just as any other derived pointer would.

#### Example

Here is an example of how to properly use this API to mess around
with tagged pointers. Here we have a tag in the lowest bit:

```rust,ignore
let my_tagged_ptr: *mut T = ...;
// Get the address and do whatever bit tricks we like
let addr = my_tagged_ptr.addr();
let has_tag = (addr & 0x1) != 0;
let real_addr = addr & !0x1;
// Reconstitute a pointer with the new address and use it
let my_untagged_ptr = my_tagged_ptr.with_addr(real_addr);
*my_untagged_ptr = ...;
```

`dynx Trait` values don’t have to be a pointer to something that implemented Trait — they just have to be something pointer-sized.

- The syntax `dyn Trait` means a pointer-sized value that implements Trait. Typically a `Box` or `&` but sometimes other things.
- The syntax `dyn[T] Trait` means “a value that is layout-compatible with T that implements Trait”; `dyn Trait` is thus sugar for `dyn[*const ()] Trait`, which we might write more compactly as `dyn* Trait`.
- The syntax `dyn[T..] Trait` means “a value that starts with a prefix of T but has unknown size and implements Trait.
- The syntax `dyn[..] Trait` means “some unknown value of a type that implements Trait”.

[Effective TypeScript](https://effectivetypescript.com/) offers a useful definition of a type in TypeScript: “Think of a type as a set of values.”
One way to define a set of values is with a class (“every value that is an instance of class X”), but of course you can define a set of values infinitely many other ways too.

A type, at its core, represents the set of possible values and the valid operations that can be done on the values.

```ts
const x = "hi"; // the type of x is “hi”
type State = "loading" | "loaded" | "error";
```

TypeScript uses structural typing.
Structural typing is about the shape of a type, whereas nominative typing is about the name. TypeScript is mostly structural.
The heart of structural typing: two types that have the same shape are effectively interchangeable.

```ts
type A = {
  value: string;
};
function my_func(a: A): string {
  return a.value;
}
my_func({ value: "hi", image: "a gzipped picture of a cat" }); // no error

// tagged union
type A = {
  value: string;
  kind: "a"; // here's the tag
};
type B = {
  value: string;
  kind: "b";
};
function my_func(a: A): string {
  return a.value;
}
my_func({ value: "hi", kind: "a" }); // no error, unsurprisingly
my_func({ value: "hi", kind: "b" }); // now this *is* an error
my_func({ value: "hi" }); // also an error
my_func({ value: "hi", kind: "a" as const, image: "a gzipped photo of a cat" }); // no error
```

Type manipulation like Partial, Required, Pick, Omit, mapped types, conditional types, and the truly wild template literal types open up a rich language of type expression.

```ts
type Account = {
  name: string;
  balance: string;
};
function makeAccount({
  name = "foo",
  balance = "10.05",
}: Partial<Account> = {}): Account {
  return { name, balance };
}

makeAccount(); // a caller can take all the default options
makeAccount({ balance: "0.00" }); // or override one or more
makeAccount({ name_with_typo: "foo" }); // TS correctly emits an error
```

The TypeScript language actually consists of two sub-languages - one is JavaScript, and the other is the type language:

- for the JavaScript language, the world is made of JavaScript values
- for the type language, the world is made of types

The type language is so expressive that it has been proven to be Turing complete.
Here I don't make any value judgment of whether being Turing complete is good or bad, nor do I know if it is even by design or by accident (in fact, often times, Turing-completeness was achieved by accident).

Sometimes type programming is jokingly referred to as “type gymnastics” when it gets really complex, fancy and far more sophisticated than it needs to be in a typical application.
They are more like academic exercises, not suitable for production applications because:

- they are hard to comprehend, especially with esoteric TypeScript features.
- they are hard to debug due to incredibly long and cryptic compiler error messages.
- they are slow to compile.

```ts
type Username = "foo";
type Matched = Username extends "foo" ? true : false; // true

type User = { name: string; age: number };
type Name = User["name"];

type Names = string[];
type Name = Names[number];

type Tuple = [string, number];
type Age = Tuple[1];

type Fn<A extends string, B extends string = "world"> = [A, B];
//   ↑    ↑           ↑                          ↑              ↑
// name parameter parameter type          default value   function body/return statement

type Result = Fn<"hello">; // ["hello", "world"]

type User = {
  name: string;
  age: number;
};

type StringifyProp<T> = {
  [K in keyof T]: string;
};

type UserWithStringProps = StringifyProp<User>; // { name: string; age: string; }

type FilterStringProp<T> = {
  [K in keyof T as T[K] extends string ? K : never]: string;
};

type FilteredUser = FilterStringProp<User>; // { name: string }

type Str = "foo-bar";
type Bar = Str extends `foo-${infer rest}` ? rest : never; // 'bar'

type FillArray<
  Item,
  N extends number,
  Array extends Item[] = []
> = Array["length"] extends N ? Array : FillArray<Item, N, [...Array, Item]>;

type Foos = FillArray<"foo", 3>; // ["foo", "foo", "foo"]
```

Here are logical steps to arrive at one solution:

1. create a generic type called FillArray (remember we talked about that generics in our type language are just like functions?)

- FillArray<Item, N extends number, Array extends Item[] = []>

2. Inside the "function body", we need to check if the length property on Array is already N using the extends keyword.

- if it has reached to N (the base case), then we simply return Array
- if it hasn't reached to N, it recurses and added one more Item into Array

Before TypeScript 4.5, the max recursion depth is 45. In TypeScript 4.5, we have tail call optimization, and the limit increased to 999.

define a variable
bind a name to some data or function
define variables or other named entities
A variable declaration statement creates a new binding that associates a name with a value, a variable expression accesses that binding.
An l-value “evaluates” to a storage location that you can assign into.
Every valid assignment target happens to also be valid syntax as a normal expression.

Native functions provide access to the fundamental services that all programs are defined in terms of.
The mechanism for users to provide their own native functions is called a foreign function interface (FFI) or native extension.

Expr, Stmt, Var

con
var
fun
mod
enum/union
struct
trait

expression-oriented

Additional passes between parsing and execution are common: variable resolution, type checking, optimizations.
Basically, preprocess any work that doesn’t rely on state that’s only available at runtime.

An instance stores state, the class stores behavior.
Field names shadow method names, a subtle but important semantic point.

A type is itself a value.
Some types can be called like functions (those that have a constructor), e.g. int and str.
Type checks are of the form type(10) == int.
Methods are now syntax sugar for calling a function scoped to a type, meaning that "hello".len() is equivalent to str.len("hello").
Support for `import` renaming with `as`.
