---
tags:
  - maths/numerical-methods
---
[[Differential Equations]]
# First Order
$$y_{r+1} \approx y_r + h \left.\frac{dy}{dx}\right|_{\displaystyle x_r}$$
$$ r \in \mathbb{N},\space x_r = x_{r-1}+h, \space h \in \mathbb{R}$$
*The way this works is that you are given initial conditions $(x_0, y_0)$. So you can compute $\left.\frac{dy}{dx}\right|_{x_0}$, then you can approximate the coordinates some $h$ away from $x_0$ by using a straight line with gradient $\left.\frac{dy}{dx}\right|_{x_0}$. To get a more accurate approximation, you can calculate the next point with smaller steps $h$. As a result, you have to do more iterations to get a point some distance from $x_0$*

You could also use the **Midpoint Formula**:

$$y_{r+1} \approx y_{r-1} + 2h \left.\frac{dy}{dx}\right|_{x_r}$$

# Second order differential equation
$$y_{r+1} \approx 2y_r - y_{r-1} + h^2 \left.\frac{d^2y}{dx^2}\right|_{\displaystyle x_r}$$
$$\left.\frac{d^2y}{dx^2}\right|_{\displaystyle x_0} \approx \frac{y_1 - 2y_0 + y_{-1}}{h^2}$$