## 1) Prove an integer a is odd iff $a^{3}$ is odd
Assume that $a$ is an odd integer. Then it can be written as $a=2k+1; k\in\mathbb{Z}$
$$\begin{align}
a^{3}=(2k+1)^{3}=(4k^{2}+4k+1)(2k+1) \\
=8k^{3}+4k^{2}+8k^{2}+4k+2k+1 \\
=8k^{3}+12k^{2}+6k+1 \\
=2(4k^{3}+6k^{2}+3k)+1 \\
=2m+1; m\in\mathbb{Z}
\end{align}$$
Since integers are closed under addition and multiplication, then $a^{3}$ is odd.

Conversely, by contrapositive, assume $a$ is even so $a=2k; k\in\mathbb{Z}$.
$$\begin{align}
a^{3}=(2k)^{3}=8k^{3} \\
=2(4k^{3}) \\
=2m; m\in\mathbb{Z}
\end{align}$$
Thus, if $a^{3}$ is odd, then a is odd by contrapositive.

## 2) Suppose $a\in\mathbb{Z}$. Prove that $14\mid a$ iff $2\mid a$ and $7\mid a$
Assume that $a$ is divisible by 2 and 7. Then a must be a multiple of 2 and is also a multiple of 7

$$\begin{align}
a=(2m)(7k); m,k\in\mathbb{Z} \\
=14(mk) \\
=14j; j\in\mathbb{Z}
\end{align}$$
Thus, a is a multiple of 14 if a is divisible by 2 and 7.

Conversley, if a is divisible by 14, then we can write a as a multiple of 14 $a=14m; m\in\mathbb{Z}$. 
$$\begin{align}
a=14m=2(7m)=7(2m)
\end{align}$$
We have shown that 14m is a multiple of 2 and a multiple of 7 since integers are closed under multiplication. Thus $14\mid a$ iff $2\mid a$ and $7\mid a$.

## 3)Show there exists a positive real number x for which $x^{2} \lt \sqrt{ x }$
a) Let  $x= \frac{1}{2}$, then $x^{2}=\frac{1}{4}$ and $\sqrt{ x }= \frac{\sqrt{ 2 }}{2}$

b) it is the counterexmple forw the statement "there exists a positive real number x for which $x^{2} \geq \sqrt{ x }$"

## 4) Give a counter example to disprove each of the following false quantified statements
#### 4a) For any sets A and B,  $P(A) - P(B) \subseteq P(A-B)$
$A=\{1,2\}$   $B=\{1, 4\}$
$A-B=\{ 2 \}$   $P(A-B)=\{ \emptyset, \{ 2 \}\}$
$P(A) - P(B)=\{ \emptyset, \{ 1 \}, \{ 2 \}, \{ 1,2 \} \}-\{ \emptyset,\{ 1 \},\{ 4 \}, \{ 1,4 \} \}=\{ \{ 2 \}, \{ 1,2 \} \}$
$P(A)-P(B) \nsubseteq P(A-B)$

#### For every positive real number a, there is a positive real number b such that $b<a$ and if $c\in\mathbb{R}^+$ then  $bc \geq c$
*Negation:* There exists a positive real number $a$ such that for all positive real numbers $b$ with $b\geq a$, there is exists a $c \in \mathbb{R}^+$ with $bc < c$.

In this case, if we can find an example where the negation is true, then the original statement must be false. We can show that that there is a specific $a$ such that for all reals $b$ with $b \geq a$, then there is a $c$ such that $bc < c$.

Counterexample: Let $a=\frac{1}{2}$ and $b$ be any positive real number greater or equal to 1/2 ($b \geq \frac{1}{2}$), then let $c=\frac{1}{2}$ such that 
$$\begin{align}
bc < c  \text{ let b=2/3}\\
\left( \frac{2}{3} \right)\left( \frac{1}{2} \right) < \frac{1}{2} \\
\frac{1}{3} < \frac{1}{2}
\end{align}$$
Therefore, the original statement must be false by counterexample.

## 5a) Prove for every non-zero real number x, there exists a real number y such that xy=1
- Only need to prove that a single example exists where this is true. Almost like disprove by counterexample, but the opposite

For all x, let $y=\frac{1}{x}$ .
$$\begin{align}
xy=1 \\
x\left( \frac{1}{x} \right)=1 \\
\frac{x}{x}=1
\end{align}$$
## 5b) Prove there exists a natural number M such that for all natural numbers n > M, $\frac{1}{n}<0.105$ 

Let $M=9.6$. For any $n>9.6$, $\frac{1}{n}<0.105$

## 6a) Disprove there exists a largest natural number M
FSOC assume that there is a largest natural number M. For every natural number m, let N = m +1. N > M. This is a contradiction since M should have been that largest number.  

## 6b) Disprove there exists a rational number x and an irrational number y such that x+y is rational
hint - first prove that the sum of two rational numbers is rational

# Extra
Prove at least four parts of the Invertible Matrix Theorem are equivalent.
https://mathworld.wolfram.com/InvertibleMatrixTheorem.html

Condition 1) By definition of linear independence, a set of vectors $\{ v_{1}\dots v_{n} \}$ are linearly independent if

$$

t_{1}v_{1} + t_{2}v_{2}+\dots+t_{n}v_{n}= 0

$$

only has the trivial solution $t_{1}=t_{2}=\dots=t_{n}=0$

**Proof:** (Condition 1 -> 2) Suppose that if the columns of A are linearly independent, then $A\vec{x}=\vec{0}$ has only the trivial solution.

  

Let $$A=\begin{bmatrix}

\vec{v_{1}} & \vec{v_{2}} & \dots & \vec{v_{n}}

\end{bmatrix} \text{ and } \vec{x}=\begin{bmatrix}

t_{1} \\

t_{2} \\

\vdots \\

t_{n}

\end{bmatrix}$$

By definition of matrix multiplication, $$A \vec{x}=\begin{bmatrix}

\vec{v_{1}} & \vec{v_{2}} & \dots & \vec{v_{n}}

\end{bmatrix} \begin{bmatrix}

t_{1} \\

t_{2} \\

\vdots \\

t_{n}
\end{bmatrix} = 0$$$$t_{1}v_{1} + t_{2}v_{2}+\dots+t_{n}v_{n}= 0$$

**Proof**: (Condition 2 -> 3) If $A \vec{x}=\vec{0}$ has only the trivial solution, then $A \to A \vec{x}$ is one to one.

A matrix is one to one if for every vector in the domain(A) it maps to exactly one vector in range(A).

Proceed with a proof by contradiction. Suppose that $A \vec{x}= \vec{0}$ has only the trivial solution and $A \vec{x}$ is not one to one. Therefore the exists a vector $a, b \in V$ and $\vec{x} \neq \vec{y}$ such that

$$\begin{align}

A \vec{a} = A \vec{b} \\

A \vec{a} - A \vec{b} = \vec{0} \\

A(\vec{a} - \vec{b})= \vec{0}

\end{align}$$

By our assumption, $A \vec{x} = \vec{0}$ if $\vec{x}$ is the zero vector, therefore $\vec{a} - \vec{b}=\vec{0}$. This is a contradiction because $\vec{a} \neq \vec{b}$. Therefore, $A \vec{x}= \vec{0}$ having only the trivial solution implies $A$ is one to one.
  

**Proof:** (Condition 3 -> 4) If $A \to A \vec{x}$ is one to one, then the nullspace is $\{ \vec{0} \}$.

Proceed with a direct proof. If A is one to one, then every input always has one output. The only input for which $A \vec{x} = \vec{0}$ is if $\vec{x}=\vec{0}$.

The nullspace is defined as $Null(A) = \{ \vec{x} : A \vec{x} = \vec{0} \}$. We know the only vector where this is the case is when $\vec{x}=\vec{0}$, therefore $Nul(A)=\{ \vec{0} \}$ as required.

  

**Proof**: (Condition 4 -> 1) If the nullspace is $\{ \vec{0} \}$ then the columns are linearly independent.

Proceed with a proof by contrapositive. If the columns are not linearly independent, then the nullspace is not equal to $\{ \vec{0} \}$.

Then $\{ v_{1}\dots v_{n} \}$ are not linearly independent if there exists at least one $t_{n}$ that is not equal to 0.

$$

t_{1}v_{1} + t_{2}v_{2}+\dots+t_{n}v_{n}= 0

$$

Let
$$\vec{x}=\begin{bmatrix}
t_{1} \\
t_{2} \\
\vdots \\
t_{n}
\end{bmatrix}$$

Therefore, there is a vector other than $\vec{0}$ that maps to 0. So the nullspace is $\{ \vec{0}, \vec{x} \}$ and is not equal to $\{ \vec{0} \}$. Therefore if the nullspace is 0, then the columns are linearly independent.