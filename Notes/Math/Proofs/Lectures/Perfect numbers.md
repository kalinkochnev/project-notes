A number is perfect if it is equal to the sum of its positive divisors less than itself.
ex: 6 = 1 + 2 + 3  X6X (don't include 6)

## Conjectures
- Perfect numbers are even (no one knows)
- Perfect numbers in 6 or 8 (if we hve an even perfect #, then it ends in 6 or 8)
- There aren't many

## Euclid's conjecture
$A=\{ 2^{n-1}(2^n-1) : n \in \mathbb{N} \wedge 2^n-1 \text{ is prime} \}$ and $P = \{  p \in \mathbb{N} \mid p \text{ is perfect} \}$

Does A = P?
1. Are the numbers in A even or odd?

$n=1$ $2^{n-1}$ is not prime thus
$$
\begin{align}
a \in A = 2^{n-1}(2^n-1); n>1 \\
=2^{>0} (2^{n}-1)
\end{align}
$$
Thus a is even

## Euclid's conjecture for only evens
https://math.stackexchange.com/questions/3116812/sum-of-increasing-powers
- If we give up looking for the odds we can show $A=P$

Assume $x \in A$, x $x=2^{n-1}(2^{n}-1)$ where $n \in \mathbb{N}$ and $2^{n-1}$ is prime. 

We want to show that x is even and perfect. Since when $x=1$ $2^{n-1}$ is not prime, $n > 1$. So $x=2^{n-1}(2^{n}-1)=2(2^{n-2}-1)(2^{n}-1)$  and n-2 > 0 **<-- why do we say n-2?**
Therefore, x is even

The divisors of $x=2^{n-1}(2^{n}-1)$ and we know $2^{n}-1$ is prime so it can either include that factor or not.

 |                  | $2^{0}$      | $2^{1}$      | $2^{2}$      | ... | $2^{n-1}$ |
 | ---------------- | ------------ | ------------ | ------------ | --- | --------- |
 | No $2^{n}-1$     | 1            | 2            | 4            | ... | $2^{n-1}$ |
 | Single $2^{n}-1$ | $1(2^{n}-1)$ | $2(2^{n}-1)$ | $4(2^{n}-1)$ | ... |    ** don't include the number itself as a part of the sum$(2^{n}-1)$ $1(2^{n}-1)$**      |

$1 + 2 + 4 + \dots + 2^{n-1} = \frac{1-2^{n}}{1-2}=2^{n}-1$
$(2^{n}-1)(1+2+\dots+2^{n-2})=(2^{n}-1)(2^{n-1}-1)$
Take the sum of both of these so
$$
\begin{align}
=(2^{n}-1)+(2^{n}-1)(2^{n-1}-1) \\
=(2^{n}-1)(1 + 2^{n-1} -1) \text{ factor out}\\ 
=(2^{n}-1)(2^{n-1}) \\
=x
\end{align}
$$
The sum of the divisors of x are equal to x, therefore x is perfect

### Version 2
Show $P \subseteq A$
Let $x \in P$. So x is an even perfect number. $x=2^{k}q$ where q is odd. You increase k until it cannot be divisible anymore. There must be at least one power of two $k \geq 1$

Let $k=n-1$ so $n \geq 2$ since k>=1
So $x=2^{n-1}q$. Show that $q=2^{n}-1$ when $2^{n}-1$ is prime
|       | 2^0    | 2^1    | 2^2    | ... | 2^{n-1}    |
| ----- | ------ | ------ | ------ | --- | ---------- |
| d1    | 2^0 d1 | 2^1 d1 | 2^2 d1 | ... | 2^{n-1} d1 |
| d2    | 2^0 d2 |        |        |     |            |
| d3    | 2^0 d3       |        |        |     |            |
| ...   |        |        |        |     |            |
| q=d_m | 2^0 d_m       |        |        |     |            | ^ccc59c

- Write the sum along the columns
$$
\begin{align}
2^0 \left( \sum_{i=1}^m d_{i} \right) + 2^1 \left( \sum d_{i} \right)+ \dots + 2^{n-1}\left( \sum d_{i} \right) \\
\left( \sum d_{i} \right)(2^0 + 2^{1}+ 2^{2} + \dots + 2^{n-1}) \\
\left( \sum d_{i} \right)(2^{n}-1) \text{ <- this is the sum of the geometric series}
\end{align}
$$
Since x is perfect
$$
\begin{align}
2x=\left( \sum d_{i} \right)(2^{n}-1) \\
2(2^{n-1}q )= \left( \sum d_{i} \right)(2^{n}-1) \\
\sum d_{i}=\frac{2^{n} q }{2^{n}-1} = \frac{2^{n}q-q+q}{2^{n}-1} \\
=q\frac{2^{n}-1}{2^{n}-1}+\frac{q}{2^{n}-1} \\
d_{1}+\dots+d_{m}=q+\frac{q}{2^{n}-1}
\end{align}
$$
- sum(d_i) must be an integer because it is the sum of divisors which are integers
- Whenevery you divide a number and it is divisible (ex 30/5), its result is also a divisor of 30. (ex 30/5=6 which is also a divisor)
- $\frac{q}{2^{n}-1}$ must be an integer and it also divides q
	- $q \mid q$ and $\frac{q}{2^{n}-1}\mid q$
- The LHS/RHS represents the sum of all divisors. q is an odd number b/c [[Perfect numbers#^ccc59c]]
- $\frac{q}{2^{n}-1}$ must be a divisor too, so it is a single element on the LHS
- 1 is always a divisor on the LHS, so it must be 
#unfinished
So $\frac{q}{2^{n}-1}=1 \to q=2^{n}-1$ ^cbb1a2
