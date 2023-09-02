- Used to show why something is false (when its negation is true)

## Universal statements $\forall x \in S, P(X)$
- Show $\exists x \in S, \sim P(x)$, give a specific example

## Conditional $\forall x, P(X) \implies Q(X)$
- Show negation $\exists x, P(X) \wedge \sim Q(X)$

## Existence statements
- Prove $\sim(\exists \in S, P(X))= \forall x \in S, \sim P(X)$
- Can use direct, contrapositive, or contradiction

**Conjecture:** there is a real number for which $x^{4}<x<x^{2}$
- We believe this is false (x is not bounded by these two)

$$
\begin{align}
\sim(\exists x \in R, x^{4} < x < x^{2}) \\
\equiv \forall x \in \mathbb{R} , \sim (x^{4} < x < x^{2})
\end{align}
$$

We will use proof by contradiction to show that the negation is true. 
Assume that $x \in R$ and $x^{4} < x < x^{2}$. We know that $x^{4} \geq 0$ and $x > x^{4} \geq 0$ (by assumption). So $x > 0$. Thus we divide by x to get
$$
\begin{align}
x^{3} < 1 < x \\
x^{3}-1 < 0 < x-1 \\
(x-1)(x^{2}+x+1) < 0 < x-1
\end{align}
$$
Since x >1 (see above), then x-1 > 0. Divide by x-1.
$$
x^{2} + x + 1 < 0
$$
This is not possible because these are all positive terms and will never add up to less than 0. Thus it is false that $\exists x \in \mathbb{R}, x ^{4} < x < x^{2}$

**Direct contradiction**:
Disprove $\exists x \in S, P(X)$
- Directly assume that there exists an x where this is true and then show there is a contradiction

# Discussion
**Conjecture:** If A, B,C are sets, then $A-(B \cap C)=(A-B) \cap (A-C)$
The statement is false. Let $A=\{ 1,2,3 \}, B=\{ 1,2 \}, C=\{ 1,3 \}$
$$
\begin{align}
A-(B\cap C) = \{ 1,2,3 \} - \{ 1 \}=\{ 2,3 \} \\
(A-B) \cap (A - C) = \{ 3 \} \cap \{  2 \} = \emptyset
\end{align}
$$

**Conjecture:** there exists integers x,y,z all greater than 1 and no two are equal, for which $x^{y}=y^{z}$

This is a true statement. Let $x=16, y=2, 8$
Then $(16)^2=2^8=256$