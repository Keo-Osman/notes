---
tags:
  - maths/calculus
aliases:
  - Differentiation
  - Differentiable
---
# Definition
The **Derivative** of $f(x)$ is 
$$
f'(x) = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h} \quad \text{or} \quad f'(a) =\lim_{x \to a}\frac{f(x)-f(a)}{x-a}
$$
A function is differentiable $\Leftrightarrow$ $f'(a)$ exists. It is Differentiable on $(a, b) \Leftrightarrow$ it is differentiable $\forall x \in (a, b)$
***
# Techniques
## Chain Rule
$$
\frac{d}{dx}[f(g(x))] = f'(g(x))g'(x)
$$
### Proof
$$
\begin{aligned}
& \text{First define } \epsilon \text{ to be the difference between the difference quotient } \frac{\Delta y}{\Delta x} \text{ and the derivative } f'(x) \text{ so} \\ 
& \qquad \epsilon = \frac{\Delta y}{\Delta x} - f'(x) \Rightarrow \Delta y = f'(x)\Delta x + \epsilon\Delta x\\ \\
& \text{ For } \Delta x = 0 \text{ we get } \\ 
& \qquad \lim_{\Delta x \to 0} \epsilon = \lim_{\Delta x \to 0} \left(\frac{\Delta y}{\Delta x} - f'(x)\right) = f'(x) - f'(x) = 0\\ 
& \text{ So defining } \epsilon = 0 \text{ when } \Delta x = 0 \text{ makes } \epsilon \text{ a continuous function of} \Delta x \\ \\
& \text{ Suppose } v = g(x) \text{ is differentiable at } a \text{ and } y = f(v) \text{ is differentiable at } b = g(a)\\

& \qquad\Delta v = g'(a)\Delta x + \epsilon_1\Delta x = [g'(a) + \epsilon_1]\Delta x \text{ where }\epsilon_1 \to 0\text{ as }\Delta x \to 0 \\ \\
& \qquad\Delta y = f'(b)\Delta v + \epsilon_2\Delta v = [f'(b) + \epsilon_2]\Delta v \text{ where }\epsilon_2 \to 0\text{ as }\Delta v \to 0 \\ \\
\qquad \Rightarrow & \qquad \Delta y = [f'(b) + \epsilon_2][g'(a) + \epsilon_1]\Delta x \text{ where }\epsilon_1 \to 0, \epsilon_2 \to 0\\ \\
\qquad\Rightarrow & \qquad \lim_{\Delta x \to 0} \frac{\Delta y}{\Delta x} = \lim_{\Delta x \to 0} [f'(b) + \epsilon_2][g'(a) + \epsilon_1] = f'(b)g'(a) = f'(g(a))g'(a)
\end{aligned}
$$
***
# [[Continuity]]
If $f(x)$ is Differentiable at $a$ then $f(x)$ is [[Continuity|Continuous]] at $a$. 
*However the converse is not necessarily true, such as $f(x) = |x|$ which is continuous at $0$ but not differentiable at $0$*
**Proof**
$$
\begin{aligned}
\text{Given} \\
f^{\prime}(a)& =\lim _{x \rightarrow a} \frac{f(x)-f(a)}{x-a} \\ \\
\text{Multiply}\\
f(x)-f(a)& =\frac{f(x)-f(a)}{x-a}(x-a) \\ \\

\text{Take Limit}\\
\lim _{x \rightarrow a}[f(x)-f(a)] & =\lim _{x \rightarrow a} \frac{f(x)-f(a)}{x-a}(x-a) \\
& =\lim _{x \rightarrow a} \frac{f(x)-f(a)}{x-a} \cdot \lim _{x \rightarrow a}(x-a) \\
& =f^{\prime}(a) \cdot 0=0\\ \\

\underline{\text{Final Proof}}\\
\lim _{x \rightarrow a} f(x) & =\lim _{x \rightarrow a}[f(a)+(f(x)-f(a))] \\
& =\lim _{x \rightarrow a} f(a)+\lim _{x \rightarrow a}[f(x)-f(a)] \\
& =f(a)+0=f(a)
\end{aligned}
$$
***
# Fermat's Theorem
If $f$ has a local **maximum** or **minimum** at $c$ then $f'(c)=0$
*The converse is not true if $f'(c) =0$ it is not necessarily a* **maximum** *or* **minimum**
INSERT PROOF
A **Critical Number** is a number $c$ in the domain of $f$ such that $f'(c) = 0$ or $f'(c)$ doesn't exist
***
# Rolle's Theorem
If $f$ is [[Continuity|Continuous]] on $[a,b]$, differentiable on $(a, b)$, $f(a) = f(b)$ then $\exists c \text{ s.t } f'(c) = 0$
INSERT PROOF
***
# Mean Value Theorem 
If $f$ is [[Continuity|Continuous]] on $[a,b]$, differentiable on $(a, b)$ then $\exists c \text{ s.t }$
$$
f'(c) = \frac{f(b)-f(a)}{b-a}
$$
This means that at some point $c$ the slop of the tangent is equal to the slope of the secant line which represents average rate of change hence the name

INSERT PROOF

***
# [[Concavity]]
1. $f''(x)>0 \ \forall x \in I\implies f$ is on $I$ (convex downward/concave upward)
2. $f''(x)<0 \ \forall x \in I \implies f$ is concave on $I$ (convex upward/convex downward)

A point $P$ on $f(x)$ is an inflection point if $f$ is continuous at $P$ and it changes direction of concavity.