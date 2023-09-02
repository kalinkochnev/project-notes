
## What is a basis measurement?
- When we want to know the probability of the quantum state being one of its basis vectors 
	- if $\ket{\psi}$ is in the z-basis, then the measurement must along be in the z-basis

- Think of it as projecting the current state onto one of the basis vectors

$\ket{\psi}=\alpha \ket{0} + \beta \ket{1}$
$P(0)=\bra{\psi}M_{0}^*M_{0}\ket{\psi} = \braket{\psi | 0} \braket{0 | 0}\braket{0 | \psi}$

Since $\braket{0 | 0}$ is 1, 
$$\begin{align}
\braket{\psi | 0}\braket{0 | \psi}  \\
= \braket{\psi | 0} \overline{\braket{0 | \psi}}  \\
= \mid \braket{\psi | 0}\mid^{2} \\
= \mid \alpha \mid^{2}
\end{align}$$
So the probability of observing $\ket{0}$ is the same as the $\alpha$ component squared. This relates to the [[Pythagorean Theorem]] because the total probability must always be 1

![[MeasurementAsProjection.png]]


## Measuring q-dits
See [[Dirac Notation#^b2b33e]]
- You can measure a system in a particular ONB $\{ \ket{v_{0}} \dots \ket{v_{n}} \}$  if you can rewrite it
- Sometimes 
$M_{x}=\sum_{i=0}^n \ket{v_{i}}\bra{_{i}}\otimes I_{B}$

1) Write $\ket{\psi}=\sum_{i=0}^n\ket{v_{i}}\otimes \ket{b_{i}}$

- You can measure in any basiswrite any vector in the basis you are measuring 
- If measuring in V basis, need v

ex: measure in x-basis
- $\ket{0}=\frac{1}{\sqrt{ 2 }}(\ket{+}+\ket{-})$
$$\begin{align}
\frac{1}{\sqrt{ 2 }}\left( \frac{1}{\sqrt{ 2 }}\ket{+}+\frac{1}{\sqrt{ 2 }}\ket{-})\ket{0}+\frac{1}{\sqrt{ 2 }}(\frac{1}{\sqrt{ 2 }}\ket{+} - \frac{1}{\sqrt{ 2 }}\ket{-}) \right) = \\
\frac{1}{2}(\ket{+} )
\end{align}$$
1) $P("v_{i}")=\braket{b_{i} | b_{i}}$
2) Post-measured state $\ket{v_{i}}\ket{b_{i}}$

## What is the difference between a general, basis, partial and projective measurement?
**general measurement** -  is any kind of measurement but there are special cases of it
**basis measurement** - is anything that measure directly on the basis of a state (which is generally easier)
**partial measurement** - is only trying to measure if it is $\ket{\psi}$ or $I-\ket{\psi}$
**projective measurement** - it is complicated, related to SVD