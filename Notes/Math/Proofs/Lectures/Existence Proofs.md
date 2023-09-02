- We can prove exists x, R(x) by just finding one that exists

## Existence and Uniqueness
- To show that something is unique, do a proof by contradiction assuming there is more than one.

**Prove:** There exists a unique function $f(x)$ such that $f'(x)=3x^2$ and $f(1)=2$.

To see that $f(x)$ exists, let $f(x)=x^3 +1$. Then $f'(x)=3x^2$ and $f(1) = 1^3 + 1 =2$ as needed.

Lets asume there is some $f_2(x)$ with $f'_2(x)=3x^2$ and $f_2(1)=2$.
Lemma: If $g'(x)=0, g(x)=c$ (from diff eq)

Consider f(x)-f_2(x). Take the derivative
$$\begin{align}
\frac{d}{dx}(f(x) -f_{2}(x))=f'(x)-f_{2}'(x) \\
= 3x^{2}-3x^{2} \\
=0 \\ \\
\text{Therefore, } f(x)-f_{2}(x)=c
\end{align}$$
Consider x=1. $$\begin{align}
f(1)-f_{2}(1)=c \\
2-2=c \\
C=0 \\
\text{so} f(x)-f_{2}(x)=0 \\
f(x)=f_{2}(x)
\end{align}$$
## Proving $\forall x\in S, P(x)$
- Is logically equivalent to "If x in S, then P(x)""
- Assume that x is fixed but arbitrary
**Example:** For every $x\in\mathbb{N}, \exists y\in\mathbb{R} s.t.xy=4$
Let $x\in\mathbb{N}$. Let $y=\frac{4}{x}$. Then $xy=x \frac{4}{x}=4$ as needed

## Constructive vs Nonconstructive proofs
- You can prove something exists without actually writing how to get it

**Prove**: There exists irrational numbers x,y for which $x^y$ is rational.
Let $x=\sqrt{ 2 }^\sqrt{ 2 }$ and $y=\sqrt{ 2 }$. We know that y is irrational, but we do not know if x is.

Case 1: If x is irrational, then $x^y=(\sqrt{ 2 }^\sqrt{ 2 })^\sqrt{ 2 }=\sqrt{ 2 }^{2}=2$. So therefore x is irrational and y is irrational, but $x^y$ is rational.

Case 2: If x is rational, then $x=\sqrt{ 2 }^\sqrt{ 2 }$ which is of the form irrational to the irrational power. This there is some number of the form $a^b$ where a,b are irrational but $a^b$ is rational. 


## Discussion
Show there exists an $n \in \mathbb{N}$ for which $11\mid(2^n-1)$
Let $n=10$. $2^{10}-1=1023=11(93)$

Prove $\forall x \exists y, x+y<0$
Let $x\in\mathbb{Z}$. Let $y=-x-1$, then 
$$\begin{align}
x+(-x-1)< 0 \\
-1 < 0
\end{align}$$