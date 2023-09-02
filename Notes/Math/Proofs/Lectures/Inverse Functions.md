- A [[Functions]] that undoes another function
- $f^{-1} \circ f(x)=x = f \circ f^{-1}(x)$
- The function must be [[Functions#Injective and Surjective functions|injective]] and [[Functions#Injective and Surjective functions|surjective]] (bijective)


# Inverse relation
Give a relation $R$ from $A$ to $B$, the **inverse relation** of R is the relation from B to A defined as $R^{-1}=\{ (y,x):(x,y) \in R \}$.

$R^{-1}$ is obtained by interchanging the elements in every ordered pair in 

# Identity function
For a set $A$, the identity function on A is $i_{A}: A\to A$ defined as $\forall x, i_{A}(x)=x$

# Example
The function $f: \mathbb{R} \to \mathbb{R}$ defined by $f(x)=x^{3}+1$ is bijective. Find its inverse

1. Solve for x
$$
\begin{align} 
y=x^{3}+1 \\
y-1=x^{3} \\
\sqrt[3]{y-1} =x \\
f^{-1}(y)=\sqrt[3]{y-1} \\
\end{align}
$$
2. Check $f^{-1} \circ f(x)=x$
$$
\begin{align}
f^{-1}(x^{3}+1)=\sqrt[3]{x^{3}+1-1} \\
=\sqrt[3]{x^{3}} \\
=x
\end{align}
$$
3. Check $f \circ f^{-1}(y)=y$
$$
\begin{align}
f(\sqrt[3]{y-1})=(\sqrt[3]{y-1})^{3}+1 \\
=y-1+1 \\
=y
\end{align}
$$

# Discussion
Can you find the inverse of $f(x)=x^{2}$? What if you restrict the domain and co-domain?
$f^{-1}(y)=\pm \sqrt{ y }$, however this is not a function. If you restrict the domain to $[0, \infty]$ then the inverse will be $f^{-1}(y)=\sqrt{ y }$

$f: \mathbb{R} \to \mathbb{R}^{\geq 0}$ (surjective)
$\hat{f}: \mathbb{R} ^{\geq 0} \to R^{\geq 0}$ (injective)
$f^{-1}: \mathbb{R}^{\geq 0} \to \mathbb{R}^{\geq 0}$ (invertible)