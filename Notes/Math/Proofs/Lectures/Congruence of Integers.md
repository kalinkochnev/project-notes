$a,b\in\mathbb{Z} \text{ and } n\in\mathbb{N}$ then they are **congruent modulo n** if $n \mid(a-b)$, aka $a \equiv b (mod \text{ n})$

- 2 integers are congruent when they have the same remainder modulo $n$
$6 \equiv 0 \text{ mod 3}$ | $9 \equiv 0 \text{ mod 3}$  | $3 \equiv 0 \text{ mod 3}$  | <- all have remainder 0 when divided by 3

- This is hard to show in proofs. Instead we show that the a number is divisible by the difference of 2 integers (difference between the two must be n in order for remainder 0)
ex: 
a=11 b=2, which is equiv to a-b=9 so $11 \equiv 2 \text{ mod 3}$ 
or another a=5 b=2 so a-b=3 so $5 \equiv 2 \text{ mod 3}$

**Proposition:** Let $a, b \in \mathbb{Z}$ and $n \in \mathbb{N}$. If $a \equiv b \text{ (mod n)}$ then $a^{2}\equiv b^{2}\text{ (mod n)}$
1. Assume that $a \equiv b \text{ (mod n)}$. Then $n | (a-b)$ #proof

**Scratchwork**:
- we want to show $n \mid a ^{2} -b^{2}$
- Equiv to $n | (a-b)(a+b)$
- We know $(a-b) = n y, y \in\mathbb{Z}$
- If we can show $(a-b)(a+b) = nx, x \in\mathbb{Z}$ then we are done

2. So, $a-b=nx, x\in \mathbb{Z}$. Multiply $(a+b)$ gives 
$$\begin{align}
(a-b)(a+b)=nx (a+b) \\
=n[x(a+b)]
\end{align}$$
Therefore, $a^{2}\equiv b^{2}\text{ (mod n)}$

## Discussion
**Prove the following**: Let $a, b, c \in \mathbb{Z}$ and $n \in \mathbb{N}$. If $a\equiv b\text{ (mod n)}$ then $ac \equiv bc\text{ (mod n)}$
[[Direct Proof]] 

**Scratch**: we know that $n \mid a-b$ and want to show that $n \mid ac-bc$

1. Assume that $a\equiv b\text{ (mod n)}$. Then $n |a-b$
2. So $a-b=nx, x\in\mathbb{Z}$ . Multiplying by $c$ gives
$$\begin{align}
a-b=nx \\
ca- c b =cnx \\
ca- c b=n(cx)
\end{align}$$
Therefore, since $cx \in \mathbb{Z}$, then by definition of congruence modulo n, $ac \equiv bc \text{ (mod n)}$
