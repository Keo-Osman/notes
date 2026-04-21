---
tags:
  - maths/linear-algebra
---
Space has no intrinsic idea of a grid/coordinate system this means that the basis [[Vectors]] $\hat{i},\hat{j}$ are just convention but you could describe the coordinate system - and in turn [[Matrices]]/[[Linear Transforms]] etc.. - with other basis vectors. In general in $n$ dimensions you can pick any $n$ vectors and describe the whole space - *as long as they are [[Vectors#Linear Independence|Linearly Independent]]*.

Given a non-standard set of basis vectors $b_{1},b_{2},\dots ,b_{n}$ we can find how to write any vector in terms of our standard bases $e_{1},e_{2},\dots ,e_{n}$. By taking a vector *expressed in terms of $b$* we find in terms of $e$ by applying the linear transform of matrix $A$ where the column vectors of $A$ are the basis vectors $b_{k}$.
We can find how to express a vector in terms of $b$ by multiplying by $A^{-1}$.

To express a transform $M$ (that is in terms of $b$) in terms of $e$ we simply compute the matrix $A^{-1}MA$
the logic behind this is that we first change our vector into a vector in terms of $b$ then apply the matrix (which is in terms of $b$ so they are compatible) then we turn the newly transformed vector back into our coordinate system by multiplying by $A^{-1}$.