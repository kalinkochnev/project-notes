- A proof technique that allows proving a statement true for an entire set

Given an open sentence $P(n)$, to prove $\forall n \in \mathbb{N}, P(n)$ show
1) P(1) is true (base case)
2) $P(k) \to P(k+1)$ **(assume that P(k) is true, then show P(k+1)**

## Example: Show $\sum_{k=1}^{n}k=\frac{n(n+1)}{2}$
### Base case $n=1$
On LHS we get $\sum_{k=1}^{n}=1$. On RHS we get $\frac{1*2}{2}=1$. Since equal, base case holds.

### Inductive step (Prove $\sum_{k=1}^{n}k=\frac{n(n+1)}{2} \to\sum_{k=1}^{n+1}k=\frac{(n+1)(n+2)}{2}$)
Assume inductive hypothesis $\sum_{k=1}^{n}k=\frac{n(n+1)}{2}$
Then $$
\begin{align}
\sum_{k=1}^{n+1}k=\sum_{k=1}^{n} k+(n+1) \\
= \frac{n(n+1)}{2}+(n+1) \\
=(n+1)\left( \frac{n}{2}+1 \right)=(n+1)\left( \frac{n+2}{2} \right)
\end{align}
$$
Thus by induction we can conclude that $n \in\mathbb{N}, \sum_{k=1}^{n}=\frac{n(n+1)}{2}$

## Show if $n \in \mathbb{Z}$ and $n \geq 0$, then $\sum_{i=0}^{n}i \cdot i! = (n+1)! - 1$
### Scratchwork
$$
\begin{align}
\sum_{i=0}^{n}i\cdot i! = 0*0! + 1*1 + 2*2! + 3*3! \\
=0+1+4+18 \\
1=(2!-1) \\
4+1=(3!-1) \\
18+4+1=(4!-1) \\
\end{align}
$$
### Base case.
Let $n=0$. Then LHS $\sum_{i=0}^{0}i \cdot i! =0(0!)=0$ and RHS $(0+1)! -1 = 0$. So both sides are equal as needed.

### Inductive step
Assume $\sum_{i=0}^{n} i(i!) =(k+1)! -1$. We want to show that $\sum_{i=0}^{k+1} i(i!)=(k+1+1)!-1$

$$
\begin{align}
\sum_{i=0}^{k+1}i(i!)=\sum_{i=0}^{k}i(i!) + (k+1)(k+1)! \\
=(k+1)! -1 + (k+1)(k+1)! \\
=(k+1)!\left[1 + k+1\right]-1 \\
=(k+2)!-1
\end{align}
$$
Thus by induction, if $n \in \mathbb{Z}, n\geq 0$ then $\sum_{i=0}^{n}i(i!)=(n+1)! - 1$ 

## Prove the inequality $2^{n}\leq 2^{n+1} - 2 ^{n-1}-1$ holds for each $n \in \mathbb{N}$
### Base case.
If n =1, then the LHS is $2^{1}=2$ and the RHS is $2^{1+1}-2^{1-1}-1=4-1-1=3$. As a result, $2 \leq 3$ which is a true statement.

### Inductive step
Let $k \geq 1$. We will show with direct proof that $2^{k} \leq 2^{k+1} -2 ^{k-1}-1$ implies $2^{k+1} \leq 2^{(k+1)+1} - 2^{(k+1)-1}-1$.

Suppose that the antecedent is true.
$$
\begin{align}
2^{k} \leq 2^{k+1}-2^{k-1}-1 \\
2(2^{k}) \leq 2(2^{k+1}-2^{k-1}-1)\text{ multiply both sides by 2} \\
2^{k+1} \leq 2^{k+2} - 2^{k} -2 \\
\end{align}
$$
- We are allowed to add $1$ to the RHS b/c it is simply making the larger quantity bigger, so $\leq$ still holds
$$
\begin{align}
2^{k+1} \leq 2^{k+2} - 2^{k} -2 + 1 \\
2^{k+1} \leq 2^{k+2} - 2^{k} - 1 \\
2^{k+1} \leq 2^{(k+1) +1} - 2^{(k+1)-1} - 1
\end{align}
$$
It follows by induction that $2^{n}\leq 2^{n+1} - 2 ^{n-1}-1$ is true for any $n \in \mathbb{N}$

## Proposition: If $n \in \mathbb{N}$ then $(1+x)^{n}\geq 1+nx$ for all $x \in \mathbb{R}$ with $x>-1$

### Base case
When $n=1$, the LHS is $(1+x)^{1}=1+x$ and the RHS is $1+x$. $1+x \leq 1+x$ is a true statement then.

### Inductive step
- We induct on $n$ for some specific $x \in \mathbb{R}$

Assume for some $k\geq1$ the statement $(1+x)^{k} \geq 1+kx$ is true for all $x \in \mathbb{R}$ with $x>-1$. We will show that this is true for $k+1$.
$$
\begin{align}
(1+x)^{k} \geq 1 +kx \\
(1+x)^{k}(1+x) \geq (1+kx)(1+x) \\
(1+x)^{k+1} \geq 1+x+kx+kx^{2} \\
(1+x)^{k+1} \geq 1+ (k+1)x+kx^{2}
\end{align}
$$
Removing the $kx^{2}$ term from the RHS still holds true. Thus $(1+x)^{k+1} \geq 1+(k+1)x$. By induction the proposition is true.

# Discussion
## If P(1) is true and $\forall n, P(n) \to P(n+1)$, why is $P(5)$ true?
P(1) is true, therefore P(2) is true.
P(2) is true therefore P(3) is true
P(3) is true therefore P(4) is true
P(4) is true therefore P(5) is true

## Find one other inductive proof and compare it to we've seen
