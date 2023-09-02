- It is like induction, except we sort of use proof by [[Proofs by Contradiction]] for our inductive step to show that the proposition is true

**Proposition**: $\forall n, P(n)$
1. Check P(1) is true
2. FSOC suppose there is a P(m) which is false
3. Find the smallest k with P(k) is false
4. Since P(k-1) is true but P(k) is false, there is a contradiction

## Example
If $n \in \mathbb{N}$, then $4 \mid 5^{n}-1$

"Base case": When n=1, $5^{n}-1=5^{1}-1=4$ and $4 \mid 4$ holds.

"Inductive step sort of"
FSOC, assume that the statement is false. That means there exists at least one $m \in \mathbb{N}$ such that P(m) is false.

Let $k$ be the smallest integer where the statement is false, i.e. $4 \nmid 5^{k}-1$.
Since $k-1 < k$, that means k-1 must be true ($4 \mid 5^{k-1}-1$). Therefore it is divisible by 4.
$$
\begin{align}
5^{k-1}-1=4m \\
5^{k}-5=5(4m) \\
5^{k}-4-1 = 4(5m) \\
5^{k}-1=4(5m+1)
\end{align}
$$
This implies that $5^{k}-1$ is divisible by 4. But by our assumption, when n=k the statement cannot be true. This is a contradiction and the negation cannot be true.

Therefore we can conclude that $4 \mid 5 ^{n}-1$   $\forall n \in \mathbb{N}$
