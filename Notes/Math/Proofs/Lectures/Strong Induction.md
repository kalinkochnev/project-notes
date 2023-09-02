- Kind of like dynamic programming and making pennies problem. You can build off of previous steps (out of order) to make larger amounts

**Propostion** $\forall n \in \mathbb{N}, P(n)$ is true
1. Prove the first case $P(1)$ (and maybe more base cases)
2. Given any integer $k\geq 1$ show $P(1) \wedge P(2) \wedge \dots \wedge P(k) \implies P(k+1)$

Show if $\forall j$ with $a \leq j \leq k$ P(j) is true, then so is P(k+1)

## Proposition: Any postage of $8$ cents or more can be made using only $3$ cents and $5$ cent stamps
### Scratch work
- We know how to make cents in the interval $8 \leq (\text{some amount}) \leq k$ and want to show how to make k+1
- if we do $k+1 = \underline{blank} + 3$, if blank=k-2 then $k+1=(k-2)+3$.
- If we know how to make k-2 cents then we know how to make k+1
- Therefore we want to ensure k-2 is in the interval  $8 \leq k-2 \leq k$ so we can make it
- Add 2 to both sides
- $10 \leq k \leq k+2$. As long as k >= 10, then we know how to make k+1 cents
- However, our inductive step works for $k\geq 10$ only, so case case needs to cover cases $8,9,10$


Proceed by strong [[Induction]].
### Base Case
When $n=8$, we can make 8 cents using $5c+3c$
When $n=9$ we can make it with $3c+3c+3c$
When $n=10$ we can make it with $5c+5c$

### Inductive step
Assume for $k \in \mathbb{N}$ and $k \geq 10$ we know how to make $j$ cents for as long as its in the interval $8 \leq j \leq k$. Consider $k+1$ cents

Since we know $k\geq 10$ then $k-2 \geq 8$.
Since $k-2\geq 8$ and $k-2 < k$, then k-2 is in the interval $8 \leq k-2 \leq k$. Therefore we know how to make it
$$
k+1 = (k-2)+3
$$
Since we know how to make k-2 cents, add 3 cents to make k+1

Thus by strong [[Induction]] we can make any amount of postage >= 8c

## Prove [[Algebra#Fundamental Theorem of Algebra]]
### 1) n > 1 has a prime factorization

**Base case:** When n=2, 2 is prime
**Inductive step:** Assume for all $2 \leq j \leq k-1$, we know $j$ has a prime factorization.
Consider $k$. Either k is prime so it is it's own prime factorization or it can be expressed as a product of factors.
$$
k=ml; 1< m,l < k
$$
$m$ and $l$ are both less than $k$ because $1$ is not a prime factor. Therefore, we know how to factor $m$ and $l$. so $k=(\text{prime factorization of m)(prime factorization of l})$

Thus any $n\geq 1$ has a prime factorization. 

### The factorization is unique
[[Number Theory#Euclid's Lemma]]

Use proof by smallest counter example.
We know that when $n=2$, the factorization is unique.
For the sake of contradiction, assume there exists some $n>2$ where there are two prime factorizations
$$
n=p_{1}p_{2}\dots p_{k} \text{ and } n=a_{1}a_{2}\dots a_{l} \text{ where } a_{i},p_{i} \text{ are prime}$$
Assume $n$ is the smallest such value where the factorization is not unique.
$p_{1} \mid n$ so $p_{1} \mid a_{1} \dots a_{l}$. Therefore $p_{1} \mid a_{i}$ for $1 \leq i \leq l$.

Divide n by $p_{1}=a_{i}$
$$
\begin{align}
\frac{n}{p_{1}}=p_{2}\dots p_{k} = a_{1}a_{2}\dots a_{i-1}a_{i+1} \dots a_{l}
\end{align}
$$
 $\frac{n}{p_{1}}$ has a unique factorization because n is the smallest such value that isn't true and we have that $\frac{n}{p_{1}}<n$.
So $p_{2} \dots p_{k}$ and $a_{1}\dots \hat{a_{i}}\dots a_{l}$ must be the same. This is a contradiction because we assumed there can't be unique factorizations. 

