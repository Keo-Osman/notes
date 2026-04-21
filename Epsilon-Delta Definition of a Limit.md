---
tags:
  - maths/calculus
---
# Finite Limit
$$
\lim_{x\to a}f(x) = L \Leftrightarrow  \forall \varepsilon > 0,  \exists \delta > 0 \\ 
\quad \text{s.t} \quad \\
0 < |x-a| < \delta \implies 0 < |f(x)-L| < \epsilon 
$$
This basically means that you can make the distance between $f(x)$ and $L$ arbitrarily small by taking the distance from $x$ to $a$ to be sufficiently small

**Left Hand Limit**
$$\lim_{x \to a^-} f(x) = L \Leftrightarrow \forall \epsilon > 0, \exists \delta > 0 \quad \text{ s.t. } \quad a - \delta < x < a \Rightarrow |f(x) - L| < \epsilon$$
**Right Hand Limit**
$$\lim_{x \to a^+} f(x) = L \Leftrightarrow \forall \epsilon > 0, \exists \delta > 0 \quad \text{ s.t. } \quad a < x < a + \delta \Rightarrow |f(x) - L| < \epsilon$$
## Boundedness by a Constant
You can solve Epsilon delta problems by bounding $f(x) < C|x-a|$ where $C$ is a constant. Since you are dealing with a limit you can expect $x$ to be within a small distance of $a$ such as a distance of $1$. For a distance of $1$ you get $\delta = \min{1, \frac{\epsilon}{3}}$ where $d$ is an arbitrary distance around $a$.

---
# Laws of Limits
Given $\displaystyle\lim_{x \to a} f(x) = L, \lim_{x \to a} g(x) = M \Rightarrow$
$$
\begin{aligned}
&\lim_{x \to a} [f(x) + g(x)] = L + M &&\lim_{x \to a} [f(x) - g(x)] = L - M\\
&\lim_{x \to a} [cf(x)] = cL &&\lim_{x \to a} x^n = a^n \\
&M \neq 0 \Rightarrow \lim_{x \to a} \frac{f(x)}{g(x)} = \frac{L}{M}
\end{aligned}
$$

---
# Infinite Limit
**Positive Infinity**
$$\lim_{x \to a} f(x) = \infty \Leftrightarrow \forall M > 0, \exists \delta > 0 \text{ s.t. } 0 < |x-a| < \delta \Rightarrow f(x) > M$$
*(If a limit tends to infinity, it does not exist; $\infty$ is not a number)*

**Negative Infinity**
$$\lim_{x \to a} f(x) = -\infty \Leftrightarrow \forall N < 0, \exists \delta > 0 \text{ s.t. } 0 < |x-a| < \delta \Rightarrow f(x) < N$$

---
# Limits at Infinity
## Definition
Let $f$ be defined on $(a,\infty)$ then $\displaystyle\lim_{x\to\infty}f(x)=L$ means that values of $f(x)$ can be made arbitrarily close by taking sufficiently large $x$.
## Precise Definitions
1. $x\to \infty , f(x) \to L$
	- Let $f$ be defined on $(a,\infty)$ then $\displaystyle\lim_{x\to\infty}f(x)=L \Leftrightarrow$ $\forall\epsilon>0$ $\exists N$ s.t. $x>N \Rightarrow |f(x)-L|<\epsilon$

2. $x\to -\infty , f(x) \to L$
	- Let $f$ be defined on $(-\infty,a)$ then $\displaystyle\lim_{x\to-\infty}f(x)=L \Leftrightarrow$ $\forall\epsilon>0$ $\exists N$ s.t. $x<N \Rightarrow |f(x)-L|<\epsilon$
3. $x\to \infty , f(x) \to \infty$
	- Let $f$ be defined on $(a,\infty)$ then $\displaystyle\lim_{x\to\infty}f(x)=\infty \Leftrightarrow$ $\forall M>0$ $\exists N$ s.t. $x>N \Rightarrow f(x)>M$
4. $x\to -\infty , f(x) \to -\infty$
	- Let $f$ be defined on $(-\infty,a)$ then $\displaystyle\lim_{x\to-\infty}f(x)=\infty \Leftrightarrow$ $\forall M<0$ $\exists N>0$ s.t. $x>N \Rightarrow f(x)<M$
## Asymptotes
The line $y=L$ is a horizontal asymptote of $y=f(x)$ if either $\displaystyle\lim_{x\to\infty}f(x)=L$ or $\displaystyle \lim_{x\to-\infty}f(x)=L$
### Slant Asymptotes
Some curves have asymptotes that are oblique, neither horizontal nor vertical.
$$\lim_{x\to\infty}[f(x)-(mx+c)]=0 \Rightarrow y=mx+c \text{ is a slant asymptote of } f(x)$$