IEEE Standard for Floating-Point Arithmetic (IEEE 754)
IEEE 754-1985 binary floating-point arithmetic algorithms
IEEE 754-2008 plus the IEEE 854-1987 Standard for Radix-Independent Floating-Point Arithmetic
IEEE 754-2019 incorporating mainly clarifications, defect fixes and new recommended operations

包含舍入误差是浮点数计算的本质特征。
The distribution of representable floating-point values resembles a logarithmic scale.

- [What's Up With Floating Point?](https://timroderick.com/floating-point-introduction/)
- [What you never wanted to know about floating point but will be forced to find out](https://www.volkerschatz.com/science/float.html)

双精度浮点数的范围最大至 ±10^308，最小至 ±10^-308，限制在 ±10^20 至 ±10^-20 的范围内期望的计算精度可达到 15 位数。

Cast f32 operands to f64 and perform the computation with f64 precision, then cast the result to f32.
