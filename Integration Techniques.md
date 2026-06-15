# Common Results

## Trig
$$
\begin{aligned}
& \int \sin (x) dx = -\cos (x) + C &&\int \cos (x) dx = \sin (x) + C \\
&\int \tan(x)\, dx = \ln|\sec(x)| + C &&\int \cot(x)\, dx = \ln|\sin(x)| + C\\ &\int \sec(x)\, dx = \ln|\sec(x) + \tan(x)| + C &&\int \csc(x)\, dx = \ln|\csc(x) - \cot(x)| + C\\
& \int \sec (x) \tan (x) dx = \sec (x) + C &&\int \sec^2 (x) = \tan (x) + C\\
&\int \csc(x) \cot(x) dx = -\csc (x) + C &&\int \csc^2 (x) dx = -\cot(x) + C\\
\end{aligned}
$$
## Inverse Trig
## Hyperbolic
$$
\begin{aligned}
& \int \sinh (x)\,dx = \cosh (x) + C &&\int \cosh (x)\,dx = \sinh (x) + C \\
& \int \tanh (x)\,dx = \ln(\cosh (x)) + C &&\int \coth (x)\,dx = \ln(\sinh (x)) + C \\
& \int \operatorname{sech}   (x)\,dx = \cot^{-1}(\sinh (x)) + C &&\int \operatorname{csch}  (x)\,dx = -\coth^{-1}(\cosh (x)) + C \\
&\int \text{sech}(x)\tanh(x)\, dx = -\operatorname{sech} (x) + C  && \int \text{sech}^2(x)\, dx = \tanh(x) + C\\
&\int \text{csch}(x)\operatorname{coth}(x) \, dx = -\operatorname{csch} (x) + C && \int \text{csch}^2(x)\, dx = -\coth(x) + C\\

\end{aligned}
$$
## Inverse Hyperbolic

$$\begin{aligned} &\int \frac{1}{1+x^2} dx = \arctan(x) + C &&\int \frac{1}{\sqrt{1-x^2}} dx = \arcsin(x) + C\\ &\int \frac{1}{\sqrt{x^2+a^2}} dx = \ln\left|x + \sqrt{x^2+a^2}\right| + C &&\int \frac{1}{\sqrt{x^2-a^2}} dx = \ln\left|x + \sqrt{x^2-a^2}\right| + C\\ &\int \frac{1}{x^2 - a^2} dx = \frac{1}{2a}\ln\left|\frac{x-a}{x+a}\right| + C &&\int \frac{1}{a^2-x^2}dx = \frac{1}{2a}\ln\left|\frac{x+a}{x-a}\right| + C\\ &\int a^x dx = \frac{a^x}{\ln a} + C &&\int \ln(x)\, dx = x\ln(x) - x + C\\  &\int \sinh(x)\, dx = \cosh(x) + C &&\int \cosh(x)\, dx = \sinh(x) + C\\ &\int \text{sech}^2(x)\, dx = \tanh(x) + C &&\int \text{csch}^2(x)\, dx = -\coth(x) + C\\ &\int \frac{1}{\sqrt{1+x^2}}\,dx = \text{arcsinh}(x) + C &&\int \frac{1}{\sqrt{x^2-1}}\,dx = \text{arccosh}(x) + C \end{aligned}$$

# Reverse Chain Rule
 $$\int f'(ax + b) dx = \frac{1}{a}f(ax + b) + C \quad \int \frac{f'(x)}{f(x)} dx = \ln{f(x)} + C \quad\int f'(x)(f(x))^n dx= \frac{1}{n+1}(f(x))^{n+1} + C$$ 
***
# Substitution
**Theorem**
Let $g :[ a, b] \to \mathbb{R}$ be continuously differentiable, and let $f$ be continuous on the range of $g$. Then:
$$
\int_{a}^{b}f(g(x))g'(x)dx = \int_{g(a)}^{g(b)}f(u)du
$$
**Proof**
Let $F$ be the antiderivative of $f$, then consider 
$$
\frac{d}{dx}F(g(x)) = F'(g(x))g'(x) = f(g(x))g'(x)
$$
Substituting this back into our integral 
$$
\int_{a}^{b}f(g(x))g'(x)dx = \int_{a}^{b} \frac{d}{dx} F(g(x))dx = F(g(b)) - F(g(a)) =  \int_{g(a)}^{g(b)}f(u)du
$$

***
# Integration By Parts
**Theorem**
$$
\int u \frac{dv}{dx} dx = uv - \int v \frac{du}{dx} dx
$$
**Proof**
This is simply a rearrangement of the product rule.

Let consider the function $u \cdot v$, then $\displaystyle\frac{d}{dx}(uv) = u\frac{du}{dx} + v \frac{dv}{dx}$ and taking the integral of both sides we get $\displaystyle uv =\int u \frac{du}{dx} + \int v \frac{dv}{dx}$ and rearrange to get $\displaystyle\int u \frac{dv}{dx} dx = uv - \int v \frac{du}{dx} dx$ as desired.
***
# Reduction 
The Reduction formula allows you to write an integral as a recurrence relation. This is generally used for integrals with high powers that would require many **integration by parts** iterations.
$$I_n = \int g(x,n)dx = \sum_{r=0}^{n-1} g_r(n)I_r$$
You can use the reduction formula in conjunction with a substitution $r = g(x)$ and the Method of Differences to compute tricky summations.
