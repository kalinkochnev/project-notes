**Def** Suppose $f: A\to B$ is a function
1. If $X \subseteq A$, the image of X is the set $f(X)={f(x) : x \in X}\subseteq B$
	- Imagine where one region gets mapped to another
1. If $Y \subseteq B$, the preimare of Y is the set $f^{-1}(Y)=\{ x \in A: f(x)  \in Y\} \subseteq A$
	- Imagine where you have a specific output region and want to know what inputs result in it
- Preimages can be defined for non-invertible functions!!
	- Image and preimage do not cancel out one another

## Theorem
Given $f: A\to B$, let $W,X \subseteq A$ and $Y,Z \subseteq B$
1. $f(W \cap X) \subseteq f(W)\cap f(X)$
2. $f(W \cup X)=f(W) \cup f(X)$
3. $X \subseteq f^{-1}(f(X))$

1. $f^{-1}(Y \cup Z)=f^{-1}(Y) \cup f^{-1}(Z)$
2. $f^{-1}(Y \cap Z)=f^{-1}(Y) \cap f^{-1}(Z)$
3. $f(f^{-1}(Y))\subseteq Y$


# Examples
### Let $f: \mathbb{R} \to \mathbb{R}$ be defined by $f(x)=x^{2}$. Find $f(\{ 0,1,2 \})$ and $f^{-1}f(\{ 0,1,2 \}))$

$f(\{ 0,1,2 \})=\{ 0,1,4 \}$
$f^{-1}(\{ 0,1,4 \})=\{ 0, -1, 1, -2, 2 \}$

$f^{-1}(f(\{ 0,1,2 \})) \neq \{ 0, 1, 2 \}$

### **Prove** $f(W \cap X) \subseteq f(W)\cap f(X)$
Let $x \in f(W\cap X)$. Then there exists an $a$ such that $f(a)=x$. Since $a \in W \cap X$, $a \in W$ and $a \in X$. 

Since $a \in W$, $f(a)=x$ then $x \in f(W)$
Since $a \subseteq X, f(a)=x$ then $x \in f(X)$
Since $x \in f(W)$ and $x \in f(X)$, then $x \in f(W) \cap f(X)$

- It is a subset and not always an equality. Counterexample:
![[Pasted image 20230413102741.png]]

# Discussion
$f: A \to B$ and $X \subseteq A$
Prove that $X \subseteq f^{-1}(f(x))$ (preimage of the image) and show an example where they aren't equal
=
Let $a \in X$. Let $f(a)=b$. Then $b \in f(X)$. So since $f(a)=b$ and $b\in f(x)$
$f^{-1}(f(x))$ contains a. So $a \in f^{-1}(f(x))$ as needed