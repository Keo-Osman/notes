---
tags:
  - maths/algebra
---
# Definitions
A function is one-to-one if it never takes the same value twice: $x_1 \neq x_2 \Rightarrow f(x_1) \neq f(x_2)$

Let $f$ be a one-to-one function with domain A and range B. Then $f^{-1}$ has domain B and range A and is defined as $f^{-1}(y) = x \Leftrightarrow f(x) = y \quad \forall y \in B$

# Properties 
$f^{-1}(f(x)) = x$ $\forall x \in A$ 
$f(f^{-1}(x)) = x$ $\forall x \in B$

The graph of $f^{-1}$ is obtained by reflecting $f$ about $y = x$

# [[Continuity]]
If $f$ is one-to-one continuous on $[a,b]$ then $f^{-1}$ is continuous on $[\min{f(a),f(b)}, \max{f(a),f(b)}]$

If $f$ is one-to-one differentiable at $a$ with $f'(a) \neq 0$ then $f^{-1}$ is differentiable at $b = f(a)$ and $f'(f^{-1}(b)) \neq 0$ equivalent to $f'(a) \neq 0$

$(f^{-1})'(b) = \frac{1}{f'(f^{-1}(b))} = \frac{1}{f'(a)}$
$(f^{-1})'(f(a)) = \frac{1}{f'(a)}$

INSERT PROOF