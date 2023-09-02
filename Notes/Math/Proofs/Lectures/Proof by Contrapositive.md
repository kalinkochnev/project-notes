- $Q \to P \neq P \to Q$
- Doing a direct proof on the contrapositive (assume $!Q$)
- It may be easier to assert !Q than P

**Prove** suppose $x\in\mathbb{Z}$. If $7x+9$ is even, then $x$ is odd
*Version 1: Direct proof* #proof
1. Assume $7x+9$ is even. Then $7x+9=2m$ for $m \in\mathbb{Z}$. Subtracting 9 from both sides gives
$$\begin{align}
7x=2n-9
\end{align}$$
**can't divide by 7 because then you wont get integers
2. Subtracting 6x gives
$$\begin{align}
x=2m-6x-10+1 \\
x=2(m-3x-5) + 1 \\
\end{align}$$
So $m-3x-5$ is an integer, so $x$ is odd.

*Version 2: Contrapositive proof* #proof
1. We will proceed by contradiction. Assume $x$ is even. Then $x=2m, m\in\mathbb{Z}$
$$\begin{align}
7x+9 = 7(2m) + 9 \\
= 14m+8+1 \\
= 2(7m+4) + 1
\end{align}$$
Where $7m+4\in\mathbb{Z}$. Thus $7x+9$ is odd

## Discussion
**Proposition**: Suppose $x\in\mathbb{Z}$. If $x^2 -6x+5$ is even, then $x$ is odd #proof

1. We will proceed with proof by contrapositive. Assume that $x$ is even, then $x=2m, m \in \mathbb{Z}$
$$\begin{align}
x^{2}-6x+5 = (2m)^{2}-6(2m)+5 \\
=4m^{2}-12m+5 \\
=2(2m^{2}-6m+2)+1 \\
\end{align}$$
Since $2m^{2}-6m+2$ is an integer (closed under addition and multiplication), then $x^2 -6x+5$ is odd. 

**Prove:** Suppose $x, y \in \mathbb{Z}$. If $5 \nmid xy$, then $5 \nmid x$ and $5 \nmid y$ #proof
- It is much easier to make the statement that x does divide xy versus does not divide. Hint to prove by contrapositive

1. We will proceed via contrapositive and [[Proofs by Cases|proof by cases]]. Assume $5 \mid x$ or $5 \mid y$ (we had to negate the AND)

*Case 1*: Let $5 \mid x$. Then $x=5a$ for $a \in \mathbb{Z}$. So
$$\begin{align}
xy=(5a)y
\end{align}
=5(ay)
$$
Then $5 \mid xy$ as needed 

*Case 2*: Let $5 | y$ . Then $y=5a$ for $a\in\mathbb{Z}$. So $xy=x(5a)=5(xa)$ where $x\in\mathbb{Z}$. Then $5 \mid xy$

In either case, when $5\mid x$ or $5 \mid y$, we get $5\mid xy$, thus by contrapositive, if $5 \nmid xy$ then $5 \nmid x$ and $5 \nmid y$.
