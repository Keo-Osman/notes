---
tags:
  - maths/calculus
---
# Maclaurin [[Series]]
The Maclaurin Series of a function is an approximation for a function at x=0. *(many common functions are exactly equal their Maclaurin expansion and are called analytical functions)*
The Maclaurin series for a function $f(x)$ that is infinitely differentiable at $x = 0$ is given by:
$$f(x) = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \frac{f'''(0)}{3!}x^3 + ... = \sum_{n=0}^{\infty} \frac{f^{(n)}(0)}{n!}x^n$$
This expansion only if $f^{(n)}(a)$ exists $\forall n \in \mathbb{N}$ and for values of $x$ for which the series converges.

***
# Taylor [[Series]]
A Taylor series is simply just a that is centred at some value $x=a$ rather than $x=0$ and is given by the formula:
$$
f(x) = \sum_{n=0}^N \frac{f^{(n)}(a)}{n!}(x-a)^n
$$
where $a$ is the $x$ value for which the Taylor Series is centred.
This expansion only if $f^{(n)}(a)$ exists $\forall n \in \mathbb{N}$ and for values of $x$ for which the series converges.