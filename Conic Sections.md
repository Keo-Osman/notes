---
tags:
  - maths/geometry
---
# Definition
Conic sections are graphs that are obtained by slicing a cone (with an inverted cone on top) with a plane
![Conic Sections|500](https://math.libretexts.org/@api/deki/files/3246/CNX_Calc_Figure_11_05_002.jfif?revision=1&size=bestfit&width=843&height=452)
# Eccentricity
For all points $P$ on a conic section, the ratio of the distance $P$ from a fixed point $F$ (the focus) and fixed straight line $D$ (the directrix) is constant. This ratio $e$ is called the eccentricity.
- If $0 \leq e < 1$, $P$ describes an ellipse
- If $e = 1$, $P$ describes a parabola
- If $e > 1$, $P$ describes a hyperbola

# Summary of Conics and Properties

| Property        | Ellipse                                                           | Parabola      | Hyperbola                                                         | Rectangular Hyperbola                       |
| --------------- | ----------------------------------------------------------------- | ------------- | ----------------------------------------------------------------- | ------------------------------------------- |
| Standard Form   | $\displaystyle\frac{x^2}{a^2} + \displaystyle\frac{y^2}{b^2} = 1$ | $y^2 = 4ax$   | $\displaystyle\frac{x^2}{a^2} - \displaystyle\frac{y^2}{b^2} = 1$ | $xy = c^2$                                  |
| Parametric Form | $(a\cos\theta, b\sin\theta)$                                      | $(at^2, 2at)$ | $(a\sec\theta, b\tan\theta)$                                      | $\left(ct, \displaystyle\frac{c}{t}\right)$ |
| Eccentricity    | $e < 1$ <br> $b^2 = a^2(1-e^2)$                                   | $e = 1$       | $e > 1$ <br> $b^2 = a^2(e^2-1)$                                   | $e = \sqrt{2}$                              |
| Foci            | $(\pm ae, 0)$                                                     | $(a, 0)$      | $(\pm ae, 0)$                                                     | $(\pm\sqrt{2}c, \pm\sqrt{2}c)$              |
| Directrices     | $x = \pm\displaystyle\frac{a}{e}$                                 | $x = -a$      | $x = \pm\displaystyle\frac{a}{e}$                                 | $x \pm y = \pm\sqrt{2}c$                    |
| Asymptotes      | none                                                              | none          | $\displaystyle\frac{y}{b} = \pm\displaystyle\frac{x}{a}$          | $x = 0, y = 0$                              |
# Parabolas
**Formed by** slicing a cone with a plane parallel to its slant
**Cartesian Equation**: $y^2 = 4ax$
**Parametric Equation**: $x = at^2$, $y = 2at$ for $t \in \mathbb{R}$
**Eccentricity**: $e = 1$
**Focus**: $(a, 0)$
**Directrix**: $x + a = 0$
# Hyperbolas
**Formed by** slicing a cone with a plane that intersects both nappes of the cone
**Cartesian Equation**: $\displaystyle\frac{x^2}{a^2} - \displaystyle\frac{y^2}{b^2} = 1$
**Parametric Equation**: $x = a\sec\theta$, $y = b\tan\theta$ or $x = a\cosh t$, $y = b\sinh t$
**Eccentricity**: $e > 1$
**Focus**: $(\pm ae, 0)$
**Directrix**: $x = \pm\displaystyle\frac{a}{e}$

**Other Properties**
$c^2 = a^2e^2 = a^2 + b^2$  where $c$ is the focal length meaning the distance from the centre to a focus
# Rectangular Hyperbolas
**Formed by** slicing a cone with a plane perpendicular to the axis of symmetry
**Cartesian Equation**: $xy = c^2$
**Parametric Equation**: $(ct, \displaystyle\frac{c}{t})$
**Eccentricity**: $e = \sqrt{2}$
**Focus**: $(\pm\sqrt{2}c, \pm\sqrt{2}c)$
**Directrix**: $x \pm y = \pm\sqrt{2}c$
# Ellipses
*For major axis on the $x$-axis meaning $a > b$ - If the major axis is the y-axis so $b>a$ swap a and b around for everything*
**Formed by** slicing a cone with a plane at an angle less than that of the cone's slant
**Cartesian Equation**: $\displaystyle\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1$
**Parametric Equation**: $x = a\cos\theta$, $y = b\sin\theta$
**Eccentricity**: $e < 1$
**Focus**: $(\pm ae, 0)$
**Directrix**: $x = \pm\frac{a}{e}$

**Other Properties**
$c^2 = a^2e^2 = a^2 - b^2$ where $c$ is the focal length meaning the distance from the centre to a focus

