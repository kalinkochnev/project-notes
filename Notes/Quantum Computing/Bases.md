## Standard vectors
$$\ket{0}=\begin{bmatrix}
1 \\
0
\end{bmatrix}, \ket{1} =\begin{bmatrix}
0 \\
1
\end{bmatrix}$$
$$\ket{+} =\begin{bmatrix}
\frac{1}{\sqrt{ 2 }} \\
\frac{1}{\sqrt{ 2 }}
\end{bmatrix}, \ket{-} = \begin{bmatrix}
\frac{1}{\sqrt{ 2 }} \\
-\frac{1}{\sqrt{ 2 }}
\end{bmatrix} $$

**Z-basis** -- the computational basis $\{\ket{0}, \ket{1}\}$
**X-basis** -- the hadamard basis $\{\ket{+} , \ket{-} \}$ ^eb270f

**Bell basis**: $\{\ket{\Phi^+}, \ket{\Phi^-}, \ket{\Psi^+}, \ket{\Psi^-}\}$
$\ket{\Phi^{\pm}}=\frac{1}{\sqrt{ 2 }} \ket{00} \pm \frac{1}{\sqrt{ 2 }} \ket{11}$
$\ket{\Psi^\pm}=\frac{1}{\sqrt{ 2 }}\ket{01}\pm \frac{1}{\sqrt{ 2 }}\ket{10}$

## Hadamard Operator
https://en.wikipedia.org/wiki/Hadamard_transform
$H\ket{0}=\ket{+}$    and    $H\ket{1} = \ket{-}$
- The hadamard operator is its own inverse. If you apply it twice, you end up back at the start
- It is NOT the change of basis from Z to X basis
- This operator must be hermitian, so its adjoint is its inverse.
- Additionally H is its own inverse, so $H^{2}=I$

