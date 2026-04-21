---
tags:
  - maths/trigonometry
---
# Definitions
Hyperbolic functions are functions with similar properties to [[Trigonometric Functions]] but are defined in terms of exponentials. They are derived from $e^{x}$ by splitting into [[Functions#Constructing Even and Odd Functions|even and odd functions]]. With 
$$
e^{x}_{\text{even}}=\cosh (x)=\frac{e^{x}+e^{-x}}{2} \quad e^{x}_{\text{odd}}=\sinh(x)= \frac{e^{x}-e^{-x}}{2}
$$
Their relation from the trig functions comes form the fact that $e^{x}$ is connected to to the trig functions for complex $x$. We can see the similarity between identities. 
$$
e^{ix}=\cos x+i\sin x \quad e^{x}=\cosh x+\sinh x
$$
And we can get a very fundamental connection between the trig functions, [[Complex Numbers]] and the hyperbolics with 
$$
\cosh(ix)=\cos x\quad\sinh (ix)=i\sin x
$$
Like the trig functions we define 4 other functions as follows
1. $\displaystyle\tanh(x) \equiv \frac{\sinh(x)}{\cosh(x)} = \frac{e^{2x} - 1}{e^{2x} + 1}$
2. $\displaystyle\operatorname{cosech}(x) \equiv \frac{1}{\sinh(x)} = \frac{2}{e^x - e^{-x}}$
3. $\displaystyle \operatorname{sech} \equiv \frac{1}{\cosh(x)} = \frac{2}{e^x + e^{-x}}$
4. $\displaystyle\coth(x) \equiv \frac{1}{\tanh(x)} = \frac{\cosh(x)}{\sinh(x)} = \frac{e^{2x} + 1}{e^{2x} - 1}$
***
# Inverse Hyperbolic Functions
| Hyperbolic function      | Inverse                                         | Natural Log Form                                                              |
| ------------------------ | ----------------------------------------------- | ----------------------------------------------------------------------------- |
| $y = \sinh(x)$           | $y = \text{arsinh}(x)$                          | $\text{arsinh}(x) = \ln(x + \sqrt{x^2 + 1})$                                  |
| $y = \cosh(x), x \geq 0$ | $y = \text{arcosh}(x), x \geq 1$                | $\text{arcosh}(x) = \pm\ln(x + \sqrt{x^2 - 1})$                               |
| $y = \tanh(x)$           | $y = \text{artanh}(x)$, $\lvert x \rvert$ $< 1$ | $\displaystyle\text{artanh}(x) = \frac{1}{2}\ln \left(\frac{1+x}{1-x}\right)$ |
# Identities and Equations
Generally given a trig identity you can find the corresponding hyperbolic identity with **Osborn's Rule**
$$\cos(x) \rightarrow \cosh(x) \quad \sin(x) \rightarrow \sinh(x) \quad \sin^2(x) \rightarrow -\sinh^2(x) \quad\sin A \sin B \rightarrow -\sinh(A)\sinh(B)$$
This only works for identities contain linear combinations of $\sin^{\alpha}x\cos^{\beta}y, \alpha, \beta, \in \{0, 1\}$ it works by substituting $x\to ix$.
***
# [[Derivatives]]
$$\begin{aligned}
&\frac{d}{dx} \sinh(x) = \cosh(x) &&\frac{d}{dx} \cosh(x) = \sinh(x) \\
&\frac{d}{dx} \tanh(x) = \text{sech}^2(x) &&\frac{d}{dx} \text{arsinh}(x) = \frac{1}{\sqrt{x^2+1}} \\
&\frac{d}{dx} \text{arcosh}(x) = \frac{1}{\sqrt{x^2-1}} &&\frac{d}{dx} \text{artanh}(x) = \frac{1}{1-x^2}
\end{aligned}$$
# [[Integration]]
$$\begin{aligned}
&\int \sinh(x) \, dx = \cosh(x) + C &&\int \frac{1}{\sqrt{a^2+x^2}} \, dx = \text{arsinh}\left(\frac{x}{a}\right) + C \\
&\int \cosh(x) \, dx = \sinh(x) + C &&\int \frac{1}{\sqrt{x^2-a^2}} \, dx = \text{arcosh}\left(\frac{x}{a}\right) + C\\
&\int \tanh(x) \ dx = \ln(\cosh(x)) + C &&\int \frac{1}{1-x^2} \, dx = \text{artanh}(x) + C 
\end{aligned}$$

