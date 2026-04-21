---
tags:
  - maths/statistics
---
**Theorem**
$$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$
*Proof:*
Using conditional probability $\displaystyle P(A|B)= \frac{P(A \cap B)}{P(B)} \implies P(A \cap B) = P(A|B)P(B)$. Similarity $\displaystyle P(B|A) = \frac{P(A \cap B)}{P(A)}\implies P(A\cap B)=P(B|A)P(A)$ .
Setting them equal to each other we get $P(B|A)P(A)=P(A|B)P(B)$ dividing through by $P(B)$ gives Bayes' Theorem\.

**Terminology**
1. $P(A)$ is called the ***Prior***. This is what our current belief/hypothesis is about $A$ is *before* we see the data/evidence. It is our starting point.
2. $P(B|A)$ is called the ***Likelihood***. It is the probability of observing the evidence if our hypothesis was true. Effectively it measures how well our hypothesis/current beliefs are *compatible* with the evidence $B$ we just observed.
3. $P(B)$ is called the ***Evidence*** *or* ***Marginal Likelihood***. This is the probability of observing $B$ across *all* possible hypotheses. It serves as a normalisation constant. 
4. $P(A|B)$ is called the ***Posterior***. This is our updated belief in our hypothesis $A$ *after* accounting for the new evidence $B$.

*Note*
Often Bayes' Theorem is written as $\text{Posterior} \propto\text{Likelihood}\times\text{Prior}$ and we leave out the normalisation factor $P(B)$ (*the evidence*). As it is often hard to compute as well as the fact that we don't have to compute it if we have *conjugacy* that is the posterior PDF is in the same *family* as the prior PDF but just with new parameter values.