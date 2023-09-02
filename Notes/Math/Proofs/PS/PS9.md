# #4) Show using induction that $\forall n \in \mathbb{N}, 6 \mid 8 ^{n} - 2^{n}$
**Base case** n =0
We want to show that $8^{n}-2^{n}$ is a multiple of 6 for n=0.
$6^{0}-2^{0}=1-1=0$
0 is a multiple of 6 because it can be expressed as $0=6(0)$. Therefore, the basecase holds.

**Inductive step:**
Assume the inductive hypothesis that $8^{n}-2^{n}=6m; m \in\mathbb{Z}$. We want to show that $6 \mid 8^{n+1} - 2 ^{n+1}$
$$
\begin{align}
6m=8^{n}-2^{n} \\
2(6m)=2\cdot 8 - 2 \cdot 2^{n} \\
6(2m) + 6 \cdot {8}^{n}=2\cdot 8 - 2 \cdot 2^{n} +6 \cdot8 ^{n} \\
=2(8^{n}-2^{n}+3 \cdot 8 ^{n}) \\
=2(4 \cdot8 ^{n} - 2^{n}) \\
=8 \cdot 8 ^{n} - 2 \cdot 2^{n} \\
6(2m + 8^{n})=8^{n+1}-2^{n+1}
\end{align}
$$
Because the natural numbers are closed under addition and multiplication, then $8^{n+1} - 2^{n+1}$ is a multiple of 6. 

Therefore, by induction, we know that $\forall n \in\mathbb{N}, 6 \mid 8^{n} - 2^{n}$

# #2) Show $\forall n \in\mathbb{N}, \frac{d}{dx}(x^{n})=nx^{n-1}$
**Base case:** n=1
LHS $\frac{d}{dx}(x^{1})=1$ by definition. The RHS is $(1)x^{1-1}=1(1)=1$. The LHS and the RHS are equal so this statement is true for n=1. 

**Inductive step:**
Assume that $\frac{d}{dx}(x^{n})=nx^{n-1}$. We will show that this holds for $\frac{d}{dx}(x^{n+1})=(n+1)x^{(n+1)-1}=(n+1)x^{n}$

$$
\begin{align}
\frac{d}{dx}(x^{n+1})=\frac{d}{dx}(x^{n}x) \\
= x^{n} \frac{d}{dx}(x) + \frac{d}{dx}(x^{n})x \text{ by the chain rule } \\
= x^{n}(1)+(nx^{n-1})x \text{ from the inductive hyp.}\\
=x^{n}+nx^{(n+1)-1} \\
=x^{n}+nx^{n}=x^{n}(1+n) \text{ as needed}
\end{align}
$$
We have shown that the derivative of $\frac{d}{dx}(x^{n+1})=(n+1)x^{n}$.

Thus, by induction, we have shown that the statement is true.

# #12) Challenge question: Show that $s_{n}=\sqrt{ 2 + \sqrt{ 2+\dots } }$ is irrational

When n=1, $s_{1}=\sqrt{ 2 }$ which is irrational.

For the sake of contradiction, assume the statement is false. That means there exists at least one $s_{n}$ such that $s_{n}$ is rational. 

Let $s_{k}$ be the first case where this is true. Since $k-1 <k$, the $k-1$ case should be irrational while the kth case is rational.

Since $s_{k}$ is rational, it can be written as $s_{k}=\frac{p}{q};p,q \in\mathbb{Z}$
$$
\begin{align}
\frac{p}{q}=\sqrt{ 2 + \sqrt{ 2+\dots } }=\sqrt{ 2 + s_{k-1} } \\
\frac{p^{2}}{q^{2}} -2=s_{k-1}
\end{align}
$$
This is a contradiction because the LHS is a rational number because they are closed under addition and multiplication. However, as we state, $s_{k-1}$ is irrational and here we show it is rational.

Thus by proof by smallest counter example, this implies that $s_{k}$ is irrational.

# 12b) Show that $s_{n}=2\cos(\frac{\pi}{2^{n+1}})$
We will proceed with a proof by induction. 

**Base case:** let n=1
$s_{1}=\sqrt{ 2 }$ and $2\cos\left( \frac{\pi}{2^{1+1}} \right)=2\cos \frac{\pi}{4}=2(\frac{\sqrt{ 2 }}{2})=\sqrt{ 2 }$. So this statement is true for the base case.

**Inductive step:**
Assume the inductive hypothesis that $s_{k}=2\cos(\frac{\pi}{2^{k+1}})$. We will show that $s_{k+1}=2\cos(\frac{\pi}{2^{k+2}})$ follows as a result.
$$
\begin{align}
s_{k}=2\cos\left( \frac{\pi}{2^{k+1}} \right)\\
s_{k}+2 = 2+2\cos\left( \frac{\pi}{2^{k+1}} \right) \\
\sqrt{ s_{k}+2 }=\sqrt{ 2+2\cos\left( \frac{\pi}{2^{k+1}} \right) } \\
=\sqrt{ 2+2\cos\left(2 \cdot \frac{\pi}{2^{k+2}} \right) } \\
=2\sqrt{ \frac{1+\cos\left(2 \cdot \frac{\pi}{2^{k+2}} \right)}{2} }
\end{align}
$$
Apply the double angle identity $\cos \theta=\sqrt{ \frac{1+\cos(2\theta)}{2} }$

$$
\sqrt{ s_{k}+2 }=2\cos\left( \frac{\pi}{2^{k+2}} \right)=s_{k+1}
$$
We have shown that $s_{k+1}=2\cos(\frac{\pi}{2^{k+2}})$ knowing $s_{k}$.

Therefore, by induction, we know that $s_{n}=2\cos(\frac{\pi}{2^{n+1}})$ for any n. 

