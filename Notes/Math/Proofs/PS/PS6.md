## 2) **Prove**: If a real number x is irrational, then 10x must be irrational #hw

1. We will show this is true with the contrapositive. Assume that $10x$ is rational, then we will show $x$ is rational.
2. Since $10x$ is rational, then it can be written as $10x=\frac{p}{q}$ where $p,q \in \mathbb{Z}$ and $q \neq 0$.
$$\begin{align}
10x=\frac{p}{q} \\
= \frac{p}{(10q)}
\end{align}$$
3. $10q$ is an integer since integers are closed under multiplication. Therefore, is x is irrational, then 10x is irrattional

## 3) What are the steps necessary to prove $(!P \wedge Q \to !R \wedge S)$ using the contrapositive
$$\begin{align}
\sim(\sim P \wedge Q) \to \sim(\sim R \wedge S) \\
(\equiv R \vee \sim S )\to (P \vee\sim Q)
\end{align}$$
We would do a prove by cases, one where we assume that R is true, and one where S is false.

## 4) Prove : if $a,b \in \mathbb{Z}$ then $(a+b)^{3} \equiv a^{3} + b^{3} \text{ (mod 3)}$
Suppose that $a,b,k \in \mathbb{Z}$. 
$$\begin{align}
(a+b)^{3}-(a^{3} + b^{3}) =(a^{2}+2ab+b^{2})(a+b) - a^{3}-b^{3} \\
=a^{3}+3a^{2}b+3ab^{2} + b^{3} - a^{3}-b^{3} \\
=3a^{2}b+3ab^{2} \\
=3(a^{2}b+ab^{2}) \\
=3m; m\in\mathbb{Z}
\end{align}$$
$(a^{2}b+ab^{2})$ is an integer and so $(a+b)^{3}-(a^{3}+b^{3})$ is a multiple of three. Therefore, $(a+b)^{3}\equiv a^{3}+b^{3}\text{ (mod 3)}$

## 5) Prove: Suppose $x,y,z \in \mathbb{Z}$ and $x\neq 0$. If $x \nmid yz$, then $x \nmid y$ and $x \nmid z$
Proceed with proof by contrapositive. Assume that $x | y$ or $x|z$. 

*Case 1:* y can be written as $y=mx, m\in\mathbb{Z}$
$$\begin{align}
yz=(mx)z \\
=(mz)x
\end{align}$$
$(mz)$ is an integer, so if $y$ is divisible by $x$, then so is $yz$

Without loss of generality, $x \mid yz$ is true if $x \mid z$. Therefore, by contrapositive if $x \nmid yz$ then $x \nmid y$ and $x \nmid z$

The converse is if $x \nmid y$ and $x \nmid z$ then $x \nmid yz$. We will show this isn't true with a counter example. 
Let $x=10, y=2, z=5$. Then
$$\begin{align}
10 \nmid 2, 10\nmid 5 \text{ but } 10 | 10
\end{align}$$

## 6) Prove by contradiction: no point inside the circle $(x-3)^2+y^{2}=6$ is on the line $y=x+1$

"if there is a point in the circle"
"for all points in the circle, then you are not on the line"
For all points in the circle it is on the line

Assume there is a point inside the circle and it is not on the line

## 9) Use the following lemma to prove that if p is prime, then $\sqrt{ p }$ is irrational
[[Number Theory#Euclid's Lemma]]

For the sake of contradiction, assume that p is prime and $\sqrt{ p }$​ is rational.
$$\begin{align}
\sqrt{ p }=\frac{a}{b}; a,b \in\mathbb{Z} \text{ and gcd(a,b)=1} \\
p=\frac{a^{2}}{b^{2}} \\
pb^{2}=a^{2}
\end{align}$$
Using Euclid's lemma, $p$ must divide $a$ . If the product of two integers $ad$ is divisible by p, then $p$ must divide a or d. But if $d=a$, then $a$ must be divisible by p. 
$$\begin{align}
a=pk, k\in\mathbb{Z}
\end{align}$$
Substitute in $pk$ for $a$.
$$\begin{align}
pb^{2}=a^{2}=(pk)^{2} \\
=p^{2}k^{2} \\
=p^{2}k^{2}
\end{align}$$
Then $b^{2}=pk^{2}$. Following the same reasoning using Euclid's lemma, since $b^{2}$ is divisible by p, then so is b. 

Since $\frac{a}{b}$ is already in its lowest terms, it is impossible for $a$ and $b$ to both be a multiple/have a factor of $p$. Our assumption must be false, therefore if p is prime, then $\sqrt{ p }$ is irrational