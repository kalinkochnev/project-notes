See [[Determinants]]
- Let $A_{i}(\vec{b})=[\vec{a_{1}} \dots \vec{b} \dots \vec{a_{n}}]$
	- The ith column is replaced with vector $\vec{b}$

# Solving for single $x_{i}$
If $A$ is square and invertible, the unique solution to $A \vec{x} = \vec{b}$ is
$$
x_{i}= \frac{\det[A_{i}( \vec{b} )]}{\det A}
$$

# Solving for $A^{-1}$
[[Handwritten Notes.pdf#page=34]]
1. Compute adjugate, aka the matrix of [[Determinants#Cofactors|co-factors]]. Note, column 1 of $\text{adj}[A]$ are the  cofactors of row 1 of $A$.
$$
\text{adj}[A] = [C_{ij}]^{-1} = \begin{bmatrix}
C_{11} & C_{21} & \dots & C_{n1} \\
C_{12}  & C_{22} & \dots & C_{n2} \\
\vdots & \vdots &  & \vdots \\
C_{1n} & C_{2n} & \dots & C_{nn}
\end{bmatrix}
$$
2. Compute the inverse by dividing by the determinant
$$
A^{-1}=\frac{1}{\det[A]}\text{adj}[A]
$$

# Proof
[[Handwritten Notes.pdf#page=33|Proof of Cramer's Rule]]

# Examples
[[Control System Engineering.pdf#page=75]]