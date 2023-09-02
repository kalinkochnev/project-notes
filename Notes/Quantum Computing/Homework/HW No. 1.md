![[hw1prob1.jpg]]
## Question (2)
Assume $\ket{\psi}$ and $\ket{\phi}$ are not orthogonal, but normalized. Show $U\ket{\psi} = \ket{\phi}$ for some unitary operator. This must also apply to a $\mathbb{C}^n$ space.

- The operator must preserve the inner product space since it is [[Complex Linear Algebra#Unitary Linear Operator | unitary linear operator]]. Meaning, the angles between vectors must be preserved
- We must build a basis for the rest of the vector space in order to be[[Tensor Product#Injective | injective]]

Let U map $\ket{\psi}$ to $\ket{\phi}$. Let $\ket{\psi_{\perp}}$ and $\ket{\phi_{\perp}}$ be orthogonal to their respective vectors, derived using Gram Schmidt.

$\braket{\psi | \psi_{\perp}}$ must equal 0. Additionally, $\braket{\phi | \phi_{\perp}}$ must also equal 0 in the output space. This results in $\braket{\phi_{\perp} | \psi_{\perp}}=\braket{\phi | \psi}$

We can express this operator in outer product form $U=\ket{\phi}\bra{\psi} + \ket{\phi_{\perp}}\bra{\psi_{\perp}}$

![[hw1prob2.png]]
*Notice the $\ket{\psi}, \ket{\phi}$ vectors are offset by 90 deg from their orthogonal counterparts*

However, $U$ only is [[Complex Linear Algebra#Unitary Linear Operator | unitary]] if the dimension is two. For an $n$ dimensional space, we apply [[Gram-Schmidt]] repeatedly to expand the orthonormal basis

Let $\ket{u_{n}}$ represent a vector in the input space and $\ket{v_{n}}$ in the output space. 

$\ket{u_{n\perp}}=\ket{u_{n}}-proj_{U}\ket{u_{n}}$ is the vector orthogonal to all vectors before it in the input space.
$\ket{v_{n\perp}}=\ket{v_{n}}-proj_{V}\ket{v_{n}}$ is the vector orthogonal to all vectors before it in the output space

Finally, $U=\ket{\phi}\bra{\psi}+\ket{\phi _{\perp}}\bra{\psi_{\perp}}+\ket{v_{1\perp}}\bra{u_{1\perp}} + \dots+\ket{v_{n\perp}}\bra{u_{n\perp}}$

We can check this is unitary by $UU^* = I$
$U^*=\ket{\psi}\bra{\phi}+\ket{\psi _{\perp}}\bra{\phi{\perp}}+\ket{u_{1\perp}}\bra{v_{1\perp}} + \dots+\ket{u_{n\perp}}\bra{v_{n\perp}}$

$$\begin{align}
UU^*=\ket{\phi}\braket{\psi | \psi}\bra{\phi} +\ket{\phi}\braket{\psi | \psi_{\perp}}\bra{\phi_{\perp}}+\dots+\ket{\phi}\braket{\psi | u_{n\perp}}\bra{v_{n\perp}} \\
+\dots + \ket{\phi_{\perp}} \braket{\psi_{\perp} | \psi_{\perp}} \bra{\phi_{\perp}} +\dots+\ket{v_{n\perp}} \braket{u_{n\perp} | u_{n\perp}}\bra{v_{n\perp}} \\
=\ket{\phi} \bra{\phi} + \ket{\phi_{\perp}} \bra{\phi_{\perp}} +\dots+\ket{v_{n\perp}}\bra{v_{n\perp}}   \\
=I
\end{align}$$
Vectors that were orthogonal to each other cancelled out and we are left with the identity matrix in the output basis

## Question (3)
We will prove that A has only non-negative real eigen values iff for all $\ket{\psi}\in\mathbb{C}^n$, it holds $\bra{\psi}A\ket{\psi} \geq 0$. 

We will prove by [[Proof by Contrapositive]]. Assume that $\bra{\psi}A\ket{\psi}<0$. We will show that this is only true with negative real eigenvalues. The eigenvalue must be real since the inequality does not apply to complex numbers. Let A be the the [[Spectral Decomposition]] of eigenvectors (which are orthonormal).
$$\begin{align}
A=\sum\lambda_{n}\ket{v_{i}} \bra{v_{i}}  \\
\end{align}$$
$$\begin{align}
\bra{\psi}A\ket{\psi}=\bra{\psi}\left( \sum \lambda_{n}\ket{v_{i}}\bra{v_{i}} \right)\ket{\psi} \\
=\sum\lambda_{n} \braket{\psi | v_{i}}\braket{v_{i} | \psi} \\ 
\end{align}$$
By the property of [[Complex Linear Algebra#Properties of inner products |inner products]], we reverse the order of $\braket{v_{i} | \psi}$ and conjugate it.
$$\begin{align}
=\sum\lambda_{n}\braket{\psi | v_{i} }\overline{\braket{\psi | v_{i}}} \\
=\sum\lambda_{n}\mid \braket{\psi | v_{i}}\mid^2
\end{align}$$
$\mid \braket{\psi | v_{i}}\mid^2$ is greater than 0 since it is the squared magnitude of two vectors. The only way for $\bra{\psi}A\ket{\psi}$ to be less than 0 is if $\lambda_{n}$ is also less than 0.  

Therefore, the contrapositive is true. Then if $\lambda_{n}$ is non-negative and real, then $\bra{\psi}A\ket{\psi} \geq 0$.

## Question (4)
We will extend the result of constructing [[POVMs (Positive Operator Valued Measures) |POVM]] to distinguish between states to a set of $\{\ket{\psi_{1}}\dots \ket{\psi_{n}}\}$ linearly independent states (not orthogonal).


Since states are probabilistic, we can't measure if state A is another state B for sure. Each POVM measurement is only indicating what the state is **not** with perfect accuracy ("never wrong"). This is possible if we take advantage of orthogonal states.

The way we can identify with complete confidence whether the thing being measured is not $\ket{\psi_{n}}$ is if we create a vector orthogonal to all states except $\ket{\psi_{n}}$. Denote this by $\ket{\phi_{n}}$.

$$\begin{align}
\braket{\psi_{i} | \phi_{i}} > 0 \\
\braket{\psi_{j} | \phi_{i}}=0, \text{ where j}\neq i
\end{align}$$
This helps because the inner product between orthogonal vectors is always 0. And in this case, if we measure any vector that is not $\ket{\psi_{n}}$, we get something along the lines of $E_{i}\ket{\psi_{j}}=\ket{\phi_{i}}\braket{\phi_{i} | \psi_{j}}=0$

$\ket{\phi_{n}}$ is derived using a similar thought to [[Gram-Schmidt]]. We can find a vector orthogonal to a set of vectors by projection (and normalize them). $$\ket{\phi_{n}} = \frac{\ket{\psi_{n}} - proj_{\{\ket{\psi_{1}}\dots \ket{\psi_{n-1}}  \}}\ket{\psi_{n}}}{\mid\ket{\psi_{n}} - proj_{\{\ket{\psi_{1}}\dots \ket{\psi_{n-1}}  \}}\ket{\psi_{n}}\mid} $$Therefore, if we have a vector that is orthogonal to all states that are not being measured, we could identify what vector the state is not.

Let $E_{n}=\ket{\phi_{n}} \bra{\phi_{n}}$ and $E_{?}=I-\sum_{n}E_{n}$. This is almost a valid POVM because $E_{?}+\sum_{n}E_{n}=I$ (is trivial to verify), but $E_{n}$ does not satisfy positive semi-definiteness. Let $\ket{x}$ be an arbitrary vector.
$$\begin{align}
\bra{x} E_{?}\ket{x}=\bra{x} I\ket{x} -\sum_{n}\braket{x | \phi_{n}}\braket{\phi_{n} | x} \\
=1- \sum_{n}\mid \braket{x | \phi_{n}}\mid^{2} \\
\end{align}  
$$
By [[Cauchy-Schwartz Inequality]] and knowing that $\ket{\phi_{n}}, \ket{x}$ are normalized
$$\begin{align}
\sum_{n}\mid \braket{x | \phi_{n}}\mid^2 \leq \sum_{n}\braket{x | x}\braket{\phi_{n} | \phi_{n}} \\
\sum_{n}\mid \braket{x | \phi_{n}}\mid^2 \leq n
\end{align}
$$
Therefore, if we multiply both sides by $p=\frac{1}{n}$ then we will satisfy the property of being a POVM. The final POVMs are
$$\begin{align}
E_{n}=\frac{1}{n}\ket{\phi_{n}} \bra{\phi_{n}} \\
E_{?}=I-\frac{1}{n}\sum_{n}E_{n} 
\end{align}$$

## Question (5)
We will prove that an isometry $U$ from $V$ to $W$ (where V is a subspace of W) can be extended to a unitary operator $\mathcal{U}$. 

$\text{dim(V)=m}$, $\text{dim(W)=n}$,  $n\geq m$

Let $\{\ket{v_{1}}\dots \ket{v_{m}}\}$ be a basis for $V$. $U$ is defined as the action on its basis states $\ket{w_{i}}=U\ket{v_{i}}$. The inner product of any two vectors in the outputs space of $U$, $\{\ket{w_{1}}\dots \ket{w_{m}}\}$, has the same inner product as any two $\ket{v_{m}}$ (as long as the same indexes) because U is an isometry. 

We define $U=\sum_{i=1}^m \ket{w_{i}}\bra{v_{i}}$

To extend the domain of $U$ from $V$ to $W$, we must "fill in" the rest of the input and output vector space so that $\mathcal{U}$ acts arbitrarily on vectors outside $V$ but still in $W$. However, it must act the same as $U$ on vectors in V. Meaning, $U$ still maps vectors to $V$ but in a higher dimensional space. 

The arbitrary vectors must preserve the inner product between itself and the rest of the basis it is in. This means that if we extend the orthogonal bases for the input space and output spaces using gram-schmidt, we must ensure the inner product would be preserved. Since vector in $\{ \ket{v_{m+1}}, \dots, \ket{v_{n}} \}$ is orthogonal to $\{ \ket{v_{1}}\dots \ket{v_{m}} \}$, and so is any vector $\{ \ket{w_{m+1}} , \dots,\ket{w_{n}}\}$ is orthogonal to $\{ \ket{w_{1}} \dots \ket{w_{m}} \}$, the inner product is preserved.

To show that the $\mathcal{U}$ is unitary, when multiplied by its conjugate it must equal the identity.
$$\begin{align}
\mathcal{U}=\sum_{a=1}^m\ket{w_{a}}\bra{v_{a}}+\sum_{b=1}^{n-m} \ket{w_{m+b}}\bra{v_{m+b}} \\
\mathcal{U}^*=\sum_{c=1}^m\ket{v_{c}}\bra{w_{c}}+\sum_{d=1}^{n-m} \ket{v_{m+d}}\bra{w_{m+d}} \\
\mathcal{UU^*}=\sum_{a=1}^m \sum_{c=1}^m\ket{w_{a}}\braket{v_{a} | v_{c}}\braket{ w_{c}}+\sum_{a=1}^{n-m} \sum_{d=1}^m \ket{w_{a}} \braket{v_{a}  | v_{m+d} }\braket{ w_{m+d}}   \\
+ \sum_{b=1}^{n-m} \sum_{c=1}^{n-m}\ket{w_{m+b}}\braket{v_{m+b}|v_{c}}\bra{w_{c}} +  \sum_{b=1}^{n-m} \sum_{d=1}^{n-m}\ket{w_{m+b}}\braket{v_{m+b}|v_{m+d}}\bra{w_{m+d}}
\end{align}$$

When $a\neq c$, then $\braket{v_{a} | v_{c}}=0$ because it is an orthonormal basis. Otherwise it is $1$ when when $a=c$. This similarly applies to the last term. However for terms 2 and 3, any vector in the extended basis will always be orthogonal to any vector in the original. Therefore, terms 2 and 3 are always 0. Then we are left with
$$
\begin{align}
\mathcal{UU^*}=\sum_{a=1}^m \ket{w_{a}}\braket{ w_{a}} +\sum_{b=1}^{n-m}\ket{w_{m+b}}\bra{w_{m+b}}
\end{align}
$$
Which is the identity matrix in the W basis 