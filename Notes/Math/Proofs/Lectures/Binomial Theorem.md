
## Prove ${n+1 \choose k+1}={n \choose k} + {n \choose k+1}$
### Method 1: Algebra
$$
\begin{align}
{n \choose k }+{n \choose k+1}=\frac{n!}{k!(n-k)!}+\frac{n!}{(k+1)!(n - k -1)!} \\
= \frac{n!}{k!(n-k)(n-k-1)!}+\frac{n!}{(k+1)k!(n - k -1)!} \\ \\
= \frac{n!}{k!(n-k-1)!} \left( \frac{1}{n-k } + \frac{1}{k+1} \right) \\
= \frac{n!}{k!(n-k-1)!} \left( \frac{k+1 + n-k}{(n-k)(k+1)} \right) \\ \\
= \frac{n!}{k!(n-k-1)!} \left( \frac{n+1}{(n-k)(k+1)} \right) \\
=\frac{(n+1)!}{(k+1)!(n-k)!} \\
= {n+1 \choose k+1}
\end{align}
$$

### Method 2: Combinatorial
- ${n+1 \choose k+1}$ = # of ways to choose k+1 items from n+1 items
- Did we choose the first element?
	- Yes <- choose k from n items ${n \choose k}$
	- No <- choose k+1 from n items ${n \choose k+1}$

![[Pasted image 20230330151551.png]]
- Binomial coefficients are the same as pascal's triangle

## Prove ${n \choose k}={n \choose n-k}$
$$
{n \choose n-k}=\frac{n!}{(n-k)!(n-(n-k))!}=\frac{n!}{(n-k)!k!}={n \choose k}
$$
- ${n \choose k}$=# ways to choose k items. Whenever we choose k items, there are n-k items remaining
- Therefore, there are ${n \choose k}$ ways to have n-k items remaining
- This results in the pascal triangle being symmetric

# Binomial Theorem
If n is a non-negative integer, then
$$(x+y)^{n}={n \choose 0}x^{n}+{n \choose 1}x^{n-1}y+{n \choose 2}x^{n-2}y^{2}+{n \choose 3}x^{n-1}y^{3}+\dots+{n \choose n-1}xy^{n-1}+{n \choose n}y^{n}$$
$$(x+y)^{n}=\sum_{k=0}^{n} {n \choose k}x^{n-k} y ^{k}$$

$(x+y)(x+y)(x+y)$ is equivalent to different depths of tree (x or y) and (x or y) and (x or y)
![[Pasted image 20230330152454.png]]

## Proof by induction
We proceed by induction.
**Base case: n=0**
$(x+y)^{0}=1$ and ${0 \choose 0}x^{0}=1$. Both are 1, therefore the base case holds.

**Inductive step:**
Assume the inductive hypothesis that  $(x+y)^{n}={n \choose 0}x^{n}+{n \choose 1}x^{n-1}y+{n \choose 2}x^{n-2}y^{2}+{n \choose 3}x^{n-1}y^{3}+\dots+{n \choose n-1}xy^{n-1}+{n \choose n}y^{n}$

We want to show that $(x+y)^{n+1}={n+1 \choose 0}x^{n+1}+{n+1 \choose 1}x^{n}y+\dots+{n+1 \choose n}xy^{n}+{n+1 \choose n+1}y^{n+1}$

$$
\begin{align}
(x+y)^{n+1}=(x+y)^{n}(x+y) \\
= ({n \choose 0}x^{n}+{n \choose 1}x^{n-1}y+\dots+{n \choose n-1}xy^{n-1}+{n \choose n}y^{n})(x+y) \\ \\
\text{distribute the x and the y} \\

={n \choose 0}x^{n+1}+{n \choose 1}x^{n}y+\dots+{n \choose n-1}x^{2}y^{n-1}+{n \choose n}xy^{n}  \\
+{n \choose 0}x^{n}y+{n \choose 1}x^{n-1}y^{2}+\dots+{n \choose n}y^{n+1} \\
\text{combine like terms knowing } {n \choose k} + {n \choose k+1} = {n+1 \choose k+1 } \\
={n \choose 0}x^{n+1}+{n+1 \choose 1}x^{n}y+{n+2 \choose 2}x^{n-1}y^{2}+\dots+{n+1 \choose n}xy^{n}+{n+1 \choose n+1}y^{n+1}
\end{align}
$$

Thus by induction, the binomial theorem holds.

# What is $(2-1)^{n}$?
$(2-1)^{n}=1^{n}=1$
$$
\begin{align}
{n \choose 0}2^{n}(-1)^{0}+{n \choose 1}2^{n-1}(-1)^{2}+{n \choose 2}2^{n-2}(-1)^{3}+\dots+{n \choose n-1}2(-1)^{n-1}+ {n \choose n}1(-1)^{n} \\

\end{align}
$$
		1
	1      1
1        2       1
$1 * 2^{3} - 2^{2}*3+2*3-1=1$
- If you apply an alternating sum in this form to the row of pascal's triangle, it will always equal 1

# Discussion
## Show $\sum_{k=0}^{n} {n \choose k}=2^{n}$
n0  n1  n2   n3 = 2n

n+1(0) n+1(1) n+1(2)  n+1(n+1)

$$
\sum_{k=0}^{n}{n \choose k}(1)^{n-k}(1)^{k}=(1+1)^{n}=2^{n}
$$