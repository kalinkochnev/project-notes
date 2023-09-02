- Need to prove in both directions $p \to q$, $q \to p$
- Can use different techniques on either direction (such as $P \to Q$ and $\sim P\to \sim Q$)

## Discussion
Prove a+b is odd iff $a^{2}+b^{2}$ is odd.

($P \to Q$) Assume that $a+b$ is odd. So $a+b=2k+1; k\in\mathbb{Z}$.
$$\begin{align}
a^{2}+b^{2}=(2k+1-b)^{2}+b^{2} \\
=(2k+1-b)(2k+1-b)+b^{2} \\
=4k^{2}+2k-2kb+2k+1-b-2kb-b+b^{2}+b^{2} \\
=4k^{2}+4k-4kb-2b+2b^{2}+1 \\
=2(k^{2}+2k-2kb-b+b^{2})+1
\end{align}$$
Because integers are closed under addition, $m=k^{2}+2k-2kb-b+b^{2}$ is an integer. Thus, $a^{2}+b^{2}$ is odd.

Conversely, by contrapositive, assume x is even so $a+b=2k; k\in\mathbb{Z}$
$$\begin{align}
a^{2}+b^{2}=(2k-b)^{2}+b^{2} \\
=4k^{2}-4kb+2b^{2} \\
=2(k^{2}-2kb+b) \\
=2m; m\in\mathbb{Z}
\end{align}$$
Thus, $a^{2}+b^{2}$ is even

## The following are equivalent (TFAE)
- Either all are true, or all are false
- By knowing the truthiness of one statement, you know the rest are not
$A\iff B\iff C\iff D$

- You can prove TFAE if you can create a cycle of equivalence
$A \to B\to C$ and then also $C \to D$ (this would require only 3 proofs vs above would require 2n)

- A proof is **extraneous** if you can remove it and still be able to prove all the statements

## Discussion
What are all the different ways to prove TFAE (A, B, C) w/o extraneous proofs

![[Pasted image 20230301102350.png]]