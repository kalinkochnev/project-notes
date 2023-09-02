## Common cases
$< 0, =0, >0$
odds and evens
primes and compoosites
multiple of n versus not
**make sure the cases cover the entire space of caess**

## "Without loss of generality"
- If a proof has two very similar cases that are essentially equivalent, you can state this

### Proposition: If $n \in \mathbb{N}$ then $1+ (-1)^n(2n-1)$ is a multiple of 4 #proof 
Suppose $n \in \mathbb{N}$ . Then either n is even or n is odd. Consider the cases separately

*Case 1*: Suppose n is even, then $n=2k$ $k \in \mathbb{Z}$. 
So $1+(-1)^{n}(2n-1) = 1 + (-1)^{2k} (4k-1)$
$$=1+ 1 (4k - 1)$$
$$ = 4k$$
Thus, $1+ (-1)^{n}(2n-1)$ is a multiple of 4 when n is even

*Case 2*: Suppose n is odd. THen $n=2k+1$ $k \in \mathbb{Z}$.
So $1+(-1)^{n}(2n-1) = 1+(-1)^{2k+1}(2(2k+1)-1)$
$$\begin{align}
= 1-(4k+1) \\
= 1-4k-1 \\
= -4k
\end{align}
$$
It is a multiple of four.

In either case, $1+(-1)^{n}(2n-1)$ is a multiple of 4


### Proposition: Every multiple of 4 equals $1+(-1)^{n}(2n-1)$ for some $n \in \mathbb{N}$ #proof

- This is an example of an existence proof (If k is a multiple of 4, then there exists $k=1+(-1)^{n}(2n-1)$)

Assume k is a multiple of 4, then $k=4a$

*Case 1*: If $a=0$ then $k=0$ let $n=1$
$$\begin{align}
=1+(-1)^{n}(2n-1) \\
=0
\end{align}$$

- A proof does not need to show how they got to the answer (scratchwork). Only shows is the case
*Case 2:* If $a < 0$, let $n=1-2a$
Then 
$$\begin{align}
=1+(-1)^{n}(2n -1) \\
= 1+(-1)^{1-2a}(2(1-2a)-1) \\
=1-(1-4a) \\
= 4a \\
=k
\end{align}$$

*Case 3:* If a > 0, let $n=2a$

## Discussion
Prove: If $n \in \mathbb{Z}$ then $5n^{2} + 3n + 7$ is odd

Assum that k is odd, so $k=2n+1$
Case 1: Let 

Case 2: Let n > 0
Let $k= \frac{5}{2} n^{2}+\frac{3}{2}n+3$

$$\begin{align}
= 2k+1 \\
= 2\left( \frac{5}{2}n^{2} + \frac{3}{2}n + 3 \right) + 1 \\
= 5n^{2}+3n + 6 + 1 \\
= 5n^{2}+3n+7
\end{align}$$
**^---- WRONG!!! because we can't assume k is an integer since there are fractions**


## Discussion solution:
Prove: If $n \in \mathbb{Z}$ then $5n^{2} + 3n + 7$ is odd

We will proceed using cases. Let $n \in Z$.

*Case 1*: Assume n is odd. Then n can be written as $n=2k+1$, $k \in Z$
So $$\begin{align}
5n^{2}+3n+7 = 5(2k+1)^2 + 3(k+1)^2 + 7 \\
= 20k^2 + 26k + 15 \\
= 2(10k^2 + 13k+7)+1 \\
\end{align}$$
Since k is in the integers, we can conclude $5n^{2} + 3n + 7$ is odd

*Case 2*: Now, let n be even. Thus $n=2k$ $k \in\mathbb{Z}$


In either case we showed we can conclude $5n^{2} + 3n + 7$ is odd





### Proposition: If two integers have opposite parity, then their sum is odd #proof
Assume $a, b \in \mathbb{Z}$ and a and b have opposite parity. Then either a is even and b is odd, or a is odd and b is even.

Case 1: Suppose a is odd and b is even
Let $a = 2k+1$ and $b=2m$ and $k,m \in \mathbb{N}$
$$\begin{align}
a+b = (2k+1) + (2m) \\
= 2k + 2m + 1 \\
= 2(k+m) + 1
\end{align}$$
Which is odd

Case 2: Suppose a is even and b is odd
Let $a=2k$ and $b=2m+1$ where $k, m \in \mathbb{N}$
$$\begin{align}
a + b = 2k + 2m + 1 \\
= 2(k+m) + 1 \\
\end{align}$$
In each case is odd.


## WLOG example:
Assume $a,b \in \mathbb{Z}$ and a and b have opposite parity. Without loss of generality, assume a is even and b is odd.

<insert single case>

