[[Handwritten Notes.pdf#page=27]]

# Computation
## Minor of a matrix
A **minor** of a matrix $A$ has a row $(k)$ and column $(l)$ removed $A_{(k, l)} \in \mathbb{R}^{(n-1)\times(n-1)}$
## Cofactors
The **cofactor** of $A$ is $C_{ij}=(-1)^{(i+j)} \det[A_{ij}]$

- The determinant of a matrix can be computed by
	1) Pick a row/column to fix
	2) Compute the sum of cofactors along that fixed row/column with coefficients of that matrix entry

**Pro tip:** ==choose the row/column that has the most number of zeros==
#### Example
Fix row 1, compute cofactors for columns $[1, n]$

Using the standard definition of determinant:
$$
\begin{align}
|A|&= a_{11}C_{11} + a_{12} C_{12} + \dots + a_{1n} C_{1n}\\
&= a_{11}\det[A_{11}] - a_{12} \det[A_{12}] + \dots + (-1)^{(1+n)} a_{1n}\det[A_{1n}] \\

\end{align}
$$
# Properties
- $\det A=\det A^T$

