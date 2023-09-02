DFT is a change of basis $(x_{0}\dots x_{n}) \to (y_{0}\dots y_{n})$

**Classical discrete FT**: $y_{k}\equiv \frac{1}{\sqrt{ N }}\sum_{j=0}^{n-1}x_{j} e^{2\pi ijk/N}$
- Converts input vector to amplitude in frequency domain
- N is # of frequencies
- $k$ is particular 

- $\omega =e^{2\pi i /N}$ can be used as a shorthand

# **Quantum fourier transform**
$$
\sum_{j=0}^{N-1}x_{j}\ket{j} \to \sum_{k-0}^{N-1}y_{k}\ket{k}  
$$
- $y_{k}$ is FT of state amplitude $x_{j}$
- QFT only affects amplitudes. Basis states remain the same

## Prep work
1. Write the state $\ket{j}$ in binary form, $j=j_{1}2^{n-1}+\dots+j_{n} 2^{0}$, or shorthand $j=j_{1}j_{2}\dots j_{n}$
**Binary fraction notation**: A fraction can be represented in binary fraction notation with $0.j_{0}j_{1}\dots j_{m}=\frac{j_{0}}{2}+\frac{j_{1}}{4}+\dots +\frac{j_{m}}{2^{m+1}}$

## Definition
$$
\ket{j_{1},\dots,j_{n}} =\frac{(\ket{0} +\omega^{(0.j_{n})}\ket{1} )\otimes (\ket{0} +\omega^{(0.j_{n-1}j_{n})}\ket{1} )\otimes \dots \otimes (\ket{0} + \omega^{(0.j_{1}j_{2}\dots j_{n})}\ket{1}  )}{2^{n/2}}
$$
- notice power of $\omega$ is a binary fraction
- All we need to compute are the binary fractions to compute transform

$R_{k}$ is the phase gate
$$
R_{k}=\begin{bmatrix}
1 & 0 \\
0 & e^{2\pi i/2^{k}}
\end{bmatrix}
$$


# Examples
## QFT of $\ket{0}$
$\ket{j}\to \text{QFT} \to \frac{1}{\sqrt{ N }}\sum_{k=0}^{n-1}\omega^{jk}\ket{k}$
Find the QFT of $\ket{0}$ with $N=2$ (across two states)
$$
\begin{align} \\
\frac{1}{\sqrt{ 2 }} \sum_{k=0}^{2^{1}-1}w^{0\cdot k}\ket{0}  \\
\frac{1}{\sqrt{ 2 }}(\omega^{0\cdot 0}\ket{0} + \omega^{0\cdot1}\ket{1}  ) \\
\frac{1}{2}(\ket{0} +\ket{1} )
\end{align}
$$



$\ket{w}=\exp($
- Fourier transform is invertible $F \star \ket{0}=F^{^{\dagger}}(F\ket{1})=\ket{1}$
- 
- If we can show $F^{^{\dagger}}F=FF^{^{\dagger}}=I$

- We use $2^{n}$ because we are using qdits now $\ket{1}, \ket{2}\dots$

- The fourier transform is just like any other linear operator
$\frac{1}{\sqrt{ 2^{n} }}\sum_{j,k=0}^{2^{n}-1}\omega^{jk} \ket{k}\bra{j}$

$$
\begin{align}
F^{^{\dagger}}F=\left(\frac{1}{\sqrt{ 2^{n} }}\sum_{j',k'=0}^{2^{n}-1}(\omega^{j'k'})^{^{\dagger}} \ket{j'}\bra{k'}\right)\left(\frac{1}{\sqrt{ 2^{n} }}\sum_{j,k=0}^{2^{n}-1}\omega^{jk} \ket{k}\bra{j}\right) \\
\frac{1}{2^{n}}\left( \sum_{k',j',k,j} \omega^{-j'k'} \ket{j'} \braket{k' | k} \bra{j} \right)
\end{align}
$$