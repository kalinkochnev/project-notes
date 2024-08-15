A matrix is skew iff $S^{T}+S=0$ (and is square and symmetric)
- An entry $d_{ij} + d_{ji} = 0$

Let $\vec{a}=(a_{x}, a_{y}, a_{z})$
$$
S(\vec{a})=\begin{bmatrix}
0 & -a_{z} & a_{y} \\
a_{z} & 0 & -a_{x} \\
-a_{y} & a_{x} & 0
\end{bmatrix}
$$

# Properties
1) It is a linear operator $S(\alpha a+ \beta b)=\alpha S(a)+\beta S(b)$
2) For any vector $a, p \in \mathbb{R}^{3}$ 
$$S(a)p=a \times p$$
3) If $R \in SO(3)$ (an orthogonal matrix) then 
$$R S(a)R^{T} = S(Ra)$$ ^5626ba
4) For any skew symmetric matrix $S$,
$$x^{T}Sx=0$$
- $Sx$ represents the cross product of some arbitrary vector with $x$
- The resulting vector will be perpendicular to the original vector, so dot product is 0

# Proof [[Skew Symmetric Matrices#^5626ba| of 3]]
We know that $R(a \times b) = Ra \times Rb$
$$
\begin{align}
RS(a)R^{T}b &=R(a \times R^{T}b) \\
&=Ra \times R R^{T}b \\
&=Ra \times b \\
&=S(Ra)b
\end{align}
$$