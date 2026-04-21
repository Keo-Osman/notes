---
tags:
  - maths/numerical-methods
---
# Simpson's Rule for Approximating [[Integration|Integrals]]
You can approximate $\int_a^b g(x) dx$ with the formula:
$$\int_a^b g(x) dx \approx \frac{h}{3}\left(y_0 + 4\sum_{k=1}^{n-1} y_{2k-1} + 2\sum_{k=1}^{n-1} y_{2k} + y_{2n}\right)$$

where $2n$ is the number of strips used to approximate the area and $h$ is the width of each strip.
This formula is derived by using quadratic curves and using the result that area of quadratic curve passing through $(x_0, y_0)$, $(x_0 + h, y_1)$, $(x_0 + 2h, y_2)$ is $\frac{1}{3}h(y_0 + 4y_1 + y_2)$. 

**Other forms:**
$$\frac{1}{3}h(\text{endpoints} + 4 \times \text{odd values} + 2 \times \text{even values})$$
$$\frac{1}{3}h(y_0 + 4(y_1 + y_3 + \ldots + y_{2n-1}) + 2(y_2 + y_4 + \ldots + y_{2n-2}) + y_{2n})$