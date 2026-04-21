---
tags:
  - maths/calculus
aliases:
  - Integral
---
# Definition
To find the area under the curve you approximate with rectangles and as number of rectangles $\to \infty$ you get an exact result.

To approximate the area under $f(x)$ on $[a,b]$ you can split into $n$ strips which will have width $\Delta x = \frac{b-a}{n}$. This divides the interval $[a,b]$ into $[x_0, x_1], [x_1, x_2], \cdots [x_{n-1}, x_n]$ where $x_0 = a$, $x_n = b$ so $x_1 = a + \Delta x$, $x_2 = a + 2\Delta x, \cdots x_n = a + n\Delta x$.

Let $x_i^{*}$ be any point in $[x_{i-1}, x_i]$. Then $\displaystyle \int_a^b f(x)dx = \lim_{n \to \infty} \sum_{i=1}^n f(x_i^{*}) \Delta x$. *Provided the limit exists any choice of* $x_i^*$ *will yield the same result.*

Using the [[Epsilon-Delta Definition of a Limit]] you get:
$$\forall \varepsilon > 0 \space \exists N \in \mathbb{Z}^+ \text { s.t. } \left|\int_a^b f(x)dx - \sum_{i=1}^n f(x_i^*) \Delta x\right| < \varepsilon \quad (\forall n > N) \land (\forall x_i^* \in [x_{i-1}, x_i])$$

***
# Properties
If $f$ is [[Continuity|Continuous]] on $[a,b]$ or $f$ has a finite number of jump discontinuities then $f$ is integrable on $[a,b]$
***
# Symmetry
Suppose $f$ is continuous on $[-a,a]$ then:
1. $f$ is even $\displaystyle \Rightarrow \int_{-a}^a f(x)dx = 2\int_0^a f(x)dx$
2. $f$ is odd $\displaystyle \Rightarrow \int_{-a}^a f(x)dx = 0$

***
# Comparisons
1. $f(x) > 0$ $\displaystyle \forall x \in [a,b] \Rightarrow \int_a^b f(x)dx > 0$
2. $f(x) > g(x)$ $\displaystyle \forall x \in [a,b] \Rightarrow \int_a^b f(x)dx > \int_a^b g(x)dx$
3. $m \leq f(x) \leq M$ $\displaystyle \forall x \in [a,b] \Rightarrow m(b-a) \leq \int_a^b f(x)dx \leq M(b-a)$ (integral is in between rectangles bounded by maximum and minimum)
4. $\displaystyle \left| \int_{a}^{b}f(x)dx \right| \leq \int_{a}^{b}|f(x)|dx$

***
# Common Results
$$
\begin{aligned}
&\int x^n dx = \frac{x^{n+1}}{n+1} + c &&\int e^x dx = e^x + c\\
&\int \frac{1}{x} dx = \ln|x| + c &&\int \cos x dx = \sin x + c \\
&\int \sin x dx = -\cos x + c &&\int \sec^2 x = \tan x + c\\
&\int \csc(x) \cot x dx = -\csc x + c &&\int \csc^2 x dx = -\cot x + c\\
&\int \sec x \tan x dx = \sec x + c
\end{aligned}
$$
# Techniques
## Reverse Chain Rule
 $$\int f'(ax + b) dx = \frac{1}{a}f(ax + b) + c \quad \int \frac{f'(x)}{f(x)} dx = \ln{f(x)}\quad\int f'(x)(f(x))^n dx= \frac{1}{n+1}(f(x))^{n+1}$$ 
## Substitution
Sometimes you can simplify an integral by changing the variable. This process is similar to using the chain rule in differentiation and is called integration by substitution.

$\displaystyle \frac{d}{dx} [F(g(x))] = F'(g(x)) \cdot g'(x)$ using $v = g(x)$
$\displaystyle \int f(g(x))g'(x) = F(g(x)) + C = F(v) + C = \int f(v)dv$

If $v = g(x)$ is differentiable with range $I$ and $f$ is continuous on $I$

$\int f(g(x))g'(x) = \int f(v)dv$
$\int_a^b f(g(x))g'(x) = F(g(b)) - F(g(a)) \Rightarrow \int_a^b f(g(x))g'(x) = \int_{g(a)}^{g(b)} f(v)dv$
$\int_{g(a)}^{g(b)} f(v)dv = F(g(b)) - F(g(a))$
## Integration By Parts
$$\int u \frac{dv}{dx} dx = uv - \int v \frac{du}{dx} dx$$

***
# Improper integrals
The integral $\int_a^b f(x)dx$ is improper if:
1. One or both of the limits are $\pm \infty$ or
2. $f(x)$ is undefined at any point in $[a,b]$

To find $\int_a^\infty f(x)dx$, consider $\int_a^t f(x)dx$ and compute the limit (if it converges) as $t \to \infty$
For an integral $\int_{-\infty}^{\infty} f(x)dx$, split into 2 integrals: $\int_{-\infty}^c f(x)dx + \int_c^{\infty} f(x)dx$ , $c \in \mathbb{R}$
# Mean Value
The mean value of a function $f(x)$ in the interval $[a,b]$ is:
$$\frac{1}{b-a} \int_a^b f(x)dx$$
This is because the integral is taking infinite samples.
If $f(x)$ has mean value $\bar{f}$ over the interval $[a,b]$ then:
1. $f(x) + k$ has mean value $\bar{f} + k$
2. $kf(x)$ has mean value $k\bar{f}$, $k \in \mathbb{R}$

***
# Reduction 
The Reduction formula allows you to write an integral as a recurrence relation. This is generally used for integrals with high powers that would require many **integration by parts** iterations.
$$I_n = \int g(x,n)dx = \sum_{r=0}^{n-1} g_r(n)I_r$$
You can use the reduction formula in conjunction with a substitution $r = g(x)$ and the Method of Differences to compute tricky summations.