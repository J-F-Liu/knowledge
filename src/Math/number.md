# 数论

# 算术基本定理，又称为正整数的唯一分解定理.

> 每个大于 1 的自然数均可写为质数的积，而且这些素因子按大小排列之后，写法仅有一种方式。

例如: 6936=2^3×3×17^2，1200=2^4×3×5^2。

## 算法
Naive and slow but simplest (check all numbers from 1 to n):
```python
>>> def factors(n):
      return [i for i in range(1, n + 1) if not n%i]
```

Slightly better (realize that there are no factors between n/2 and n):
```python
>>> def factors(n):
      return [i for i in range(1, n//2 + 1) if not n%i] + [n]

>>> factors(45)
[1, 3, 5, 9, 15, 45]
```

Much better (realize that factors come in pairs, the smaller of which is no bigger than sqrt(n)):
```python
>>> from math import sqrt
>>> def factor(n):
      factors = set()
      for x in range(1, int(sqrt(n)) + 1):
        if n % x == 0:
          factors.add(x)
          factors.add(n//x)
      return sorted(factors)

>>> for i in (45, 53, 64): print( "%i: factors: %s" % (i, factor(i)) )

45: factors: [1, 3, 5, 9, 15, 45]
53: factors: [1, 53]
64: factors: [1, 2, 4, 8, 16, 32, 64]
```

More efficient when factoring many numbers:
```python
from itertools import chain, cycle, accumulate # last of which is Python 3 only

def factors(n):
    def prime_powers(n):
        # c goes through 2, 3, 5, then the infinite (6n+1, 6n+5) series
        for c in accumulate(chain([2, 1, 2], cycle([2,4]))):
            if c*c > n: break
            if n%c: continue
            d,p = (), c
            while not n%c:
                n,p,d = n//c, p*c, d + (p,)
            yield(d)
        if n > 1: yield((n,))

    r = [1]
    for e in prime_powers(n):
        r += [a*b for a in r for b in e]
    return r
```
