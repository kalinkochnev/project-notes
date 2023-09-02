## Spectral Decomposition
- iff A is symmetric, then it is orthogonally diagonalizeable
- The eigenvectors must be orthonormal and linearly independent

## Tensor Product
https://www.dpmms.cam.ac.uk/~wtg10/tensors3.html
https://kconrad.math.uconn.edu/blurbs/linmultialg/tensorprod.pdf
https://math.stackexchange.com/questions/1107523/help-understanding-tensor-products

**https://math.stackexchange.com/a/61919/873153**
$V \otimes W$ is a [[Bilinear Map]] that maps a pair $(v,w); v\in V, w\in W$ to a *single* element of $V \times W \to Z$ where $Z$ is another vector space defined to be the the tensor product space

### Motivation
https://math.stackexchange.com/a/1107535/873153
-  $V\otimes W$ allows us to study bilinear maps $\omega:V\times W\to Z$ as linear maps $\tilde\omega :V\otimes W\to Z$ on a space like $V\times W$ but with the bilinearity 'built-in'
- Then bilinear maps become linear algebra, essentially 
- Works for multilinear maps $\omega : V_1\times\dots\times V_n\to Z$ as well ($\tilde\omega : V_1\otimes\dots\otimes V_n\to Z$).
- The properties of tensor products are defined in order to make it a vector subspace, but it does follow logically from bilinear maps

### Relation to the cartesian product
- The basis elements for Z **ARE ALL** the elements in $V \times W$ ([[Cartesian Product |see cartesian product]])
If $V=W=\mathbb{R}$, then one basis element is (1,0); another (2,0); another (3,0), etc

- Think of $\ket{v_{n}} \otimes \ket{w_{n}}=\ket{v_{n} w_{n}}$ ([[Dirac Notation|shorthand tensor product]]) as indexing the set $\mid V \times W\mid$

### Elements within the subspace E
- Let E by the subspace spanned by a linear combination of tensors (the basis vectors formed by VxW)
- Not every vector in the tensor space can be written as $v \otimes w$ (a pure tensor). The elements in the space Z/subspace E are linear combinations of the pure tensors

### Dimension of tensor product
$dimZ=\mid V \times W\mid$

### Properties
1. $(\ket{v_{1}}+\ket{v_{2}}) \otimes \ket{w} = \ket{v_{1}}\otimes \ket{w} + \ket{v_{2}}\otimes \ket{w}$
2.  $\alpha \ket{v} \otimes \ket{w} = (\alpha \ket{v}) \otimes  \ket{w} = \ket{v} \otimes (\alpha \ket{w})$
3. $\ket{v}\otimes (\ket{w_{1}}+ \ket{w_{2}})=\ket{v}\ket{w_{1}}+\ket{v}\ket{w_{2}}$ 
4. $A\otimes B(\ket{\psi}\otimes \ket{\phi})=A\ket{\psi}\otimes B\ket{\phi}$
5. $(A\otimes B)^* = A^* \otimes B^*$

- These properties follow directly if you express $\ket{v}$ in terms of its basis and $\ket{w}$ in terms of its basis. 

### Kronecker product
$$\ket{v}= \begin{bmatrix}
\alpha_{1} \\

\alpha_{n}
\end{bmatrix}$$
$$\ket{w}=\begin{bmatrix}
\beta_{1} \\
\beta_{n}\\
\end{bmatrix} $$
$$\ket{v} \otimes \ket{w} = \begin{bmatrix}
\alpha_{1}\ket{w} \\
\alpha_{2}\ket{w} \\
\alpha_{n}\ket{w}  
\end{bmatrix} =\begin{bmatrix}
\alpha_{1} \beta_{1} \\
\alpha_{2}\beta_{1} \\
\alpha_{n} \beta_{1}  \\
\dots \\
a_{1} \beta_{2} \\
a_{2}\beta_{2} \\
a_{n} \beta_{2} \\ \\
\dots \\
a_{n}\beta_{n}
\end{bmatrix}$$


### Inner product w/ Tensor
- "left on left, right on right" when "distributing" each part of the tensor
$$\begin{align}
IP(\sum_{i}\alpha_{i}\ket{v_{i}}\otimes \ket{w_{i}}, \sum_{j}\beta_{j}\ket{x_{j}} \otimes \ket{y_{j}} \\
=\sum_{i,j}\alpha_{i}^*\beta_{j}(\bra{v_{i}}\otimes \bra{w_{i}})( \ket{x_{j}}\otimes \ket{y_{j}}) \\
= \sum_{i,j} \alpha_{i}^* \beta_{j}\braket{v_{i} | x_{j}}\braket{w_{i} | y_{j}} 
\end{align}$$
### What does tensor inner product represent? $(\bra{v}\otimes \bra{w})(\ket{x}\otimes \ket{y})=\braket{v | x}\braket{w | y}$
- A measure of how two tensors (joint vectors) are to one another
- Depends on similarity on individual subspaces
- Also depends on whole b/c particles that are relatively similar to one another may not be similar jointly


### [[Properties of complex numbers#Conjugate|Conjugate]] of tensor
$\left( \sum_{i}\alpha_{i}\ket{v_{i}}\otimes \ket{w_{i}} \right)^* =\sum_{i}\alpha_{i}^* \bra{v_{i}}\otimes \bra{w_{i}}$

### ONB from tensor product
Let $\{\ket{v_{1}}\dots \ket{v_{n}}\}$ be ONB for V, $\{\ket{w_{1}}\dots \ket{w_{m}}\}$ ONB for W
Then $\{\ket{v_{i}} \otimes \ket{w_{j}}\}$ is an ONB of $V \otimes W$
$\text{dim}V\otimes W=nm$

1. Show orthogonal and normalized (let a,b other other vectors in the set)
$$\begin{align}
\braket{w_{i},w_{j} | v_{a},w_{b}}=\braket{v_{i} | v_{a}}\braket{w_{j} | w_{b}} \\
=\text{1 or 0 if i=a or j=b}
\end{align}
$$
2. Show it spans $V\otimes W$
$$\begin{align}
\left( \sum_{i}\alpha_{i}\ket{v_{i}} \right) \otimes \ket{w}=\sum\alpha_{i}\ket{v_{i}} \ket{w_{i}} \\
=\sum_{i}\alpha_{i}\ket{v_{i}} \otimes \left( \sum_{j}\beta_{j}\ket{w_{j}}  \right) \\
= \sum_{i,j}\alpha_{i}\beta_{j}\ket{v_{i},w_{j}} 

\end{align}$$
We have shown that every tensor product can be written in terms of the basis vectors in $V, W$


## Isometry
An isometry is always an orthogonal matrix

