# Inner Product
Most people are familiar with the dot product where you multiply pairs of vector components and add them togehter. This is only true for a real vector space.

Inner product of real vectors

$$\braket{a  |  b } = \begin{bmatrix}
a_1 & \dots & a_{n}
\end{bmatrix} \begin{bmatrix}
b_{1} \\
\vdots \\
b_{n}
\end{bmatrix} = a_{1}b_{1}+a_{2}b_{2}+\dots + a_{n}b_{n}$$

## Product of complex vectors
However, when $\braket{ a}$ and $\ket{b}$ are complex vectors, then we need to reconsider this definition.

We want the inner product to be a function that is maximized when two vectors are most aligned with each other. As we know with the dot product is $a \cdot a = a_{1}^2 + a_{2}^2 +\dots+ a_{n}^2 = \mid a\mid^2$

With the complex plane, we similarly want to maximize the inner product when the two vectors are most similar. So we conjugate one of the vectors. Let us define the inner product function where $f(a, \bar{b})$ is the outer product and the second argument is conjugated.

If we remember, the product of a complex number $z$ and its conjugate $\bar{z}$ is
$$(a+bi)(a-bi) = a^{2} + b^{2}$$
This should start ringing some bells. The magnitude of a vector with two components is equivalent to $\sqrt{ a^{2} + b^{2} }$. Therefore the magnitude of a complex number is 
$$\mid z\mid=\sqrt{ a^{2}+b^{2} }$$
Going back to our goal, we want the inner product to be maximized when two vectors have components that are closest to one another. If we define the squared magnitude of a vector $\ket{x} \in \mathbb{C^n}$ as
$$\braket{x | x} = x_{1} \overline{x_1} + \dots+ x_{n} \overline{x_{n}}$$
Each complex component, $x_{1} \dots x_{n}$ is maximized when multiplied by its conjugate. We can't get a dot product any larger than the magnitude of $\braket{x |x}$ 

## Properties of inner products
To summarize
1. The second argument in the inner product is always considered linear
$$\left( \ket{v} ,\sum_{i}\lambda_{i}\ket{w_{i}} \right) =\sum_{i}\lambda_{i}(\ket{v} , \ket{w_{i}} )$$
2. Flipping the order of the vectors is equivalent to conjugating with the unflipped order
$$
(\ket{v} , \ket{w} )=(\ket{w} ,\ket{v} )^*
$$
3. The inner product of a vector with itself is real. $(\ket{v} ,\ket{v} )\geq 0$ and only equals 0 when $\ket{v}=0$

# Unitary Linear Operator
A unitary linear operator is one that preserves the inner product across transformations, meaning if there are two vectors $\ket{a}$ and $\ket{b}$, the value of $\braket{a | b}$ is the same across transformations. You can think of it as the angle and scale of the two vectors remains the same.

Surjective (one to one) and is an isometry (preserves inner product)

Example: if there are two vectors that are at right angles to one another, it remains a right angle even after a transformation.

# Hermitian adjoint
A unitary linear operator is an orthogonal matrix (one with columns that are orthogonal and normalized). Additionally, the unitary linear operator has the property that its inverse is the [Hermitian Adjoint](https://en.wikipedia.org/wiki/Hermitian_adjoint) . This is the generalized case where the space is the complex plane, but for the reals, it is just $U U^T=I$
$$U U^* =U^* U = I$$

The hermitian adjoint is equivalent to taking the conjugate and the transpose of a matrix.
$$(\overline{U})^T$$

## Properties of Hermitian Adjoint
1. $(A+B)^*=A^* + B^*$
2. $(AB)^* = B^* A^*$ (flip order and conjugate)


### Adjoint on outer product form #proof
[[Outer Product]]: $(\ket{v}\bra{w})^* =$
1. Flip order, conjugate

$$\bra{w}^* \ket{v}^*$$
2. Take adjoint of vector
$$\ket{v}\bra{w}$$


## Unitary Linear Operator Proof #proof
We want to prove that the hermitian adjoint of a unitary linear operator is equivalent to its inverse. Meaning if we multiply $U$ by its adjoint, we should get the identity matrix

$$U=\begin{bmatrix}
\ket{u_{1}}  & \dots  & \ket{u_{n}} 
\end{bmatrix}, U^* = \begin{bmatrix}
\braket{ u_{1}} \\
\vdots \\
\bra{ u_{n}}   \\

\end{bmatrix}$$
where $\ket{u_1} ... \ket{u_n}$ are all orthonormal.

$$U^* U =\begin{bmatrix}
\bra{u_{1}} \\
\vdots \\
\bra{ u_{n}}   \\

\end{bmatrix}\begin{bmatrix}
\ket{u_{1}}  & \dots  & \ket{u_{n}} 
\end{bmatrix} = \begin{bmatrix}
\braket{u_{1}  |  u_{1} }  & \dots & \braket{u_{1} | u_{n} } \\
\vdots & \vdots & \vdots \\
\braket{u_{n} | u_{1}} & \dots &  \braket{u_{n} | u_{n}}
\end{bmatrix} = \begin{bmatrix}
1 & 0 & \dots & 0 \\
0 & 1 & \dots & 0 \\
\vdots & \vdots & \ddots & \vdots \\

0 & 0 & \dots & 1
\end{bmatrix} = I$$
Since we know that the vectors are orthonormal, if we multiply two different vectors with each other, we know that they are orthogonal and their [[Dirac Notation#Inner Product]] is 0.

However, if we vector is multiplied with itself, that is equivalent to the squared magnitude of that vector. Since they are all unit length, the inner product is 1.

So in this matrix, all the inner products along the diagonal evaluate to 1 and everywhere else it evaluates to 0.

### Positive operators
Nielsen 71