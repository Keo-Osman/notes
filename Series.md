---
tags:
  - maths/calculus
---
# Common Results 
 $$
 \begin{aligned}
 &\sum_{r=1}^n m=mn  &&\sum_{r=1}^n r=\frac{1}{2} n(n+1) \\
&\sum_{r=k}^n f(r)=\sum_{r=1}^n f(r)-\sum_{r=1}^{k-1} f(r)  &&\sum_{r=1}^n k f(r)= k\sum_{r=1}^n f(r) \\
& \sum_{r=1}^n(f(r)+g(r))=\sum_{r=1}^n f(r)+\sum_{r=1}^n g(r) &&\sum_{r=1}^n r^2=\frac{1}{6}n(n+1)(2 n+1)\\
&\sum_{r=1}^n r^3=\frac{1}{4} n^2(n+1)^2\\
\end{aligned}
$$

***
# The Method of Differences

If the general term of a series can be describes as $u_r = f(r) - f(r+1)$ then $$\sum_{r=1}^{n}{u_r} = f(1) - f(n+1)$$
This is because when summing the $-f(n+1)$ for $n = a$ cancels with the next term’s: $f(n)$ where $n = a+1$ so you get $f(a+1) - f(a+1) = 0$ so every term cancels except the first and last.
You can apply this to $u_n = f(n) - f(n+k)$ but less terms will cancel.