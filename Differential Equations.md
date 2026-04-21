---
tags:
  - maths/calculus
---
# First Order [[Derivatives|Differential]] Equations
## Separating The Variables
Equations in the form $\displaystyle \frac{dy}{dx} = f(x)g(y)$ can be solved with $$\int \frac{1}{g(y)} dy = \int f(x) dx$$
## Integrating Factor
An integrating factor is an $f(x)$ that you multiply through by to solve differential equations in the form $\displaystyle \frac{dy}{dx} + P(x)y = Q(x)$. The general integrating factor is $f(x) = \displaystyle e^{\int P(x)dx}$ but it can be other functions
$$
\begin{aligned}
& \displaystyle \frac{dy}{dx} + P(x)y = Q(x) \\
&& \times f(x) \\
& \displaystyle f(x)\frac{dy}{dx} + f(x)P(x)y = f(x)Q(x) \\
&& \text{by properties of integrating factor} \\
& \displaystyle f(x)\frac{dy}{dx} + f'(x)y = G(x) \\
&& \text{revese chain rule} \\
& LHS = \frac{d}{dx}(f(x)y) \\
&& \text{intgrating and dividing through by} f(x) \\
& y = \frac{\int G(x)dx}{f(x)}
\end{aligned}
$$
## Coupled First-Order Simultaneous Differential Equations
$$\frac{dx}{dt} = ax + by + f(t) \quad \frac{dy}{dt} = cx + dy + g(t)$$
You can solve these equations by rearranging equation (1) to get $y = p\displaystyle\frac{dx}{dt} + qx + h(t)$ then differentiate that and sub $\displaystyle\frac{dy}{dt}$ into equation 2 to get a 2nd order differential equation, then solve for $x$, differentiate and plug into $y = p\displaystyle\frac{dx}{dt} + qx + h(t)$ to get $y$.  
You could also solve for $y$ first

---
# Second Order Differential Equations
## Homogeneous
A second order homogeneous differential equation is a linear differential equation with a 2nd derivative term that equals zero
$$a \frac{d^2 y}{dx^2} + b \frac{dy}{dx} + c y = 0$$
It has the general solution $y = Ae^{\lambda x} + Be^{\mu x}$ where  $A$ and $B$ are arbitrary constants, and $\lambda$ and $\mu$ are constants to be determined.
Plugging in $y = Ae^{\lambda x} + Be^{\mu x}$ into the differential equation, we get that $\lambda$ and $\mu$ are solutions to the quadratic equation $am^2 + bm + c = 0$ this is called the ***auxiliary equation*.** 

This quadratic leads to 3 cases.
- The auxiliary equation has 2 real root. $y = Ae^{\lambda x} + Be^{\mu x}$
- The auxiliary equation has 1 repeated root $\alpha$. $y = (A + Bx) e^{\alpha x}$
- The auxiliary equation has two complex conjugate roots $\alpha, \beta = p \pm qi$. $y = e^{px} \left( A \cos qx + B \sin qx \right)$ - *This is equivalent to the first case with complex $\lambda$ and $\mu$*
## Non-Homogeneous
A second order non-homogeneous differential equation is a linear differential equation with a 2nd derivative term that equals some function of $x$
$$a \frac{d^2y}{dx^2} + b \frac{dy}{dx} + c y = f(x)$$
It has the general solution  $y = C.F + P.I$. Where $C.F$ is the solution to the corresponding homogenous function and $P.I$ is a **particular integral**
### Particular Integral
The particular integral $(P.I)$ is a specific function that satisfies the differential equation.
To find the $P.I$, assume  $P.I = g(x)$ that has the same form as $f(x)$, then plug it into the original equation to find the coefficients.

If the particular integral contains terms which form part of the complementary function you have to modify your $P.I$ so that no 2 terms in the general solution have the same form this is done by multiplying the $P.I$ by $x$ or $x^n$

| Form of $f(x)$                    | Form of $P.I$                             |
| --------------------------------- | ----------------------------------------- |
| $p$                               | $\lambda$                                 |
| $p+q x$                           | $\lambda+\mu x$                           |
| $p+q x+r x^2$                     | $\lambda+\mu x+v x^2$                     |
| $p \mathrm{e}^{k x}$              | $\lambda \mathrm{e}^{k x}$                |
| $p \cos \omega x+q \sin \omega x$ | $\lambda \cos \omega x+\mu \sin \omega x$ |
| $px^ne^{kx}$                      | $(\lambda + \mu x+ \cdots +vx^n)e^kx$     |

---
# Series Solutions of Differential Equations
You can use Taylor series to approximate solutions to Differential Equations that can't be solved with other techniques.
Suppose you have the equation $\displaystyle\frac{dy}{dx} = f(x,y)$ and you have initial conditions $x = x_0, y = y_0$ Then you can calculate $\displaystyle\frac{dy}{dx}\bigg|_{\displaystyle x_0}$ by substitution into $f(x,y)$. By successive differentiation of the original equation and substitution of previously found values, you can find values of $\displaystyle\frac{d^ny}{dx^n}\bigg|_{\displaystyle x_0}$
Therefore the series expansion of $\displaystyle\frac{dy}{dx} = f(x, y)$ is $$y = \sum_{n=1}^N \frac{(x-x_0)^n}{n!}\frac{d^ny}{dx^n}\bigg|_{\displaystyle x_0}$$

---
# Modelling with Differential Equations
## Simple Harmonic Motion
$$\dot{x} = \frac{dx}{dt}, \quad \ddot{x} = \frac{d^2x}{dt^2}$$
 Simple harmonic motion **(S.H.M)** is motion in which acceleration is always towards a fixed point $O$ *(the centre of oscillation)*, and proportional to the displacement *(basically oscillating through a point)*.
 
**S.H.M** is modelled with $\ddot{x} = -\omega^2 x$, where $\omega$ is angular velocity 

$$\ddot{x} = \frac{dv}{dt} = \frac{dx}{dt} \times \frac{dv}{dx} = v\frac{dv}{dx} $$
$$\begin{matrix}
\displaystyle \frac{d^2x}{dt^2} + \omega^2x = 0 \\
m^2+\omega^2 = 0 \\
m =\pm \omega i \\
x = A\cos\omega t + B\sin \omega t \\
x = R\sin(\omega t + \alpha)
\end{matrix}$$
## Damped and Forced Harmonic Motion
You can refine and make more accurate models for harmonic motion by adding an additional damping force. $$\frac{d^2x}{dt^2} + k \frac{dx}{dt} + \omega^2 x = 0\quad \text{or}\quad\ddot{x} + k \dot{x} + \omega^2 x = 0$$
The auxiliary equation leads to 3 cases:
1. $k^2 > 4\omega^2$: Known as **heavy damping** - *no oscillations as resistive force is large compared to restoring force*
2.  $k^2 = 4\omega^2$: Known as **critical damping** - *again no oscillations performed*
3. $k^2 < 4\omega^2$: Known as **light damping** - *there are oscillations of which the amplitude  decreases exponentially over time*

For heavy and critical damping, the exact nature of the motion depends on initial conditions. For light damping, the period of observed oscillations can be calculated.