# 1: How are quantum states described?
Any quantum state for a closed system (every state is known) is represented as a normalized vector.

# 2: How does a quantum system evolve over time?
Any operation on a quantum state must be a [[Complex Linear Algebra#Unitary Linear Operator| unitary linear operator]].  This is derived from Schrodinger's Equation.

# 3: How are Quantum measurements made?
## What is a measurement?
If we have a quantum state of $\ket{\psi} = \alpha \ket{0} + \beta \ket{1}$, the coefficients of the basis $\ket{0}$ and $\ket{1}$ represent some superposition (an inbetween state) of $\ket{0}$ and $\ket{1}$. Or in linear algebra terms, it is a linear combination of the two vectors. 

We want to measure what state the quantum system "collapses" to. Before we measure, the system is in some inbetween state. After measurement, it is either or.

With the definition of $\ket{\psi}$, there is a certain probability of either $\ket{0}$ or $\ket{1}$ (which we will derive shortly). 

## How do we make a measurement?
There are certain outcomes that we are interested in measuring. The simplest example is knowing if the system collapses to $\ket{0}$ or $\ket{1}$, so two outcomes.

What we need to do is define a "measurement operator", $M_x$ for every outcome $x$ . 

The set of all measurements operators (one for each outcome to measure)
$$\{M_{x}\}_{x \in \text{all outcomes}}$$
There is a restriction on what kind of meaurement operator we can define. The following must be true
$$\sum_{x \in X} M_{x}^* M_{x} = I$$
For each measurement operator, the sum of all the measurement operators applied to its adjoint must add up to one. This is in order to maintain a probability distribution (the sum of all outcomes must add up to 1). 

## Outcome
The measurement operator is a mapping from $M: V \to V$. It outputs a vector in $V$ space.

### Post measured state
Measuring the outcome $x$ on vector $\ket{\psi}$
$$M_{x}\ket{\psi} $$
The **post measured state** is the quantum state of the system after measurement. Since the application of a measurement collapses the system, $M_{x}\ket{\psi}$ is not necessarily a quantum state since it may not be normalized.

The post measured state $\ket{\psi _{x}}$ is defined as simply the normalized vector measurement.
$$\ket{\psi_{x}} =\frac{M_{x} \ket{\psi _{x}} }{\sqrt{ \braket{M_{x} \ket{\psi _{x}}  | M_{x} \ket{\psi _{x}}}}} $$
These are a lot of symbols, but if we break it down, let the measurement outcome be $\ket{\psi_{O}} = M_{x} \ket{\psi_{x}}$
$$\ket{\psi_{x}} = \frac{\ket{\psi_{O}} }{\sqrt{\braket{\psi_{O} | \psi_{O}} }} = \frac{\ket{\psi_{O}} }{\mid\mid \ket{\psi_{O}} \mid\mid}$$
### Probability of outcome $x$
The probability of measuring outcome $x$ is simply the squared magnitude of the measuredment outcome $\ket{\psi_{O}} = M_{x} \ket{\psi_{x}}$

$$P(x)=\braket{\psi_{O} | \psi_{O}} $$
Since we take the conjugate of the second argument, this results in taking the adjoint of $M_x$ and $\ket{\psi_{x}}$ 
$$\braket{\psi_{O} | \psi_{O}} = IP(M_{x}\ket{\psi_{x}}, \overline{M_{x}\ket{\psi_{x}}}) = M_{x}\ket{\psi_{x}} \bra{\psi_{x}} M_{x}^* = \bra{\psi_{x}} M_{x}^*   M_{x}\ket{\psi_{x}}  $$


Quantum measurements are always with respect to some basis. 
We want to define a set of outcomes that we would like to measure. 

Quantum measurements are probabilistic.

## Phase
**Global phase**
- Relative phase is the phase between two basis vectors
$$a\ket{0} +e^{i\theta} a \ket{1} $$
- Global phase you can pull out of every basis vector
$$\ket{\psi}  \to e^{i\theta}\ket{\psi} $$
- The probability of measuring $\ket{\psi}$ or $e^{i\theta}\ket{\psi}$ are identical. Doesn't effect probability distribution
$$
\begin{align} \\
p_{G}(i)= \text{ w/ global phase}
=(\bra{\psi} U^* e^{-i\theta}M_{i}^*) (M_{i} e^{i\theta}U\ket{\psi}) \\
=e^{i\theta} e^{-i\theta} (\bra{\psi} U^* M_{i}^*M_{i} U\ket{\psi}) \\
=\bra{\psi} U^* M_{i}^*M_{i} U\ket{\psi} \\
= p(i) = \text{ w/o global phase}
\end{align} 
$$
### How does a vector end up picking up a phase? What's the point?
- phase is anything of form $e^{i\theta}$
- it is something picked up exploring possible paths
- the algorithms try to get phases to cancel out in order to collapse onto an answer

## Does measurement depend on the algorithm?
- Algorithms can operate in whatever basis as long as you change to the [[Bases#^eb270f|z-basis]] before measurement
![[AlwaysMeasinZ.png]]
#### Example:
- Probablity of measuring state i in B basis is $p(i) = |\braket{\psi | v_{i}} |^{2}$
- Let U convert psi in the B basis to the Z basis. $\ket{\psi} \to U \ket{\psi} = \ket{\phi}$
$\dot{p(i)} = | \braket{i | \phi} |^{2}= |\bra{i} U \ket{\psi} |^{2} = | \bra{i} \left( \sum_{j=1}^{n} \ket{j}\bra{b_{j}} \right) \ket{\psi} | ^{2}$

- If i and j are orthogonal, then 0. Othwerwise 1, so 
$$\dot{p(i)}=\mid \braket{b_{i}|\psi } \mid^{2}$$


# 4: Combining 2 systems
$\ket{\psi} \in \mathbb{C}^n$, $\ket{\mu} \in \mathbb{C}^n$
- The state space of a composite system is the [[Linear Algebra#Tensor Product| Tensor Product]] of the individual spaces.
- Joint state: $\ket{\psi} \otimes  \ket{u}$
- See more [[Entangled systems]]

## Q-bit dimension
Two qbits: $\mathbb{C}^2 \otimes \mathbb{C}^2 \cong \mathbb{C}^4$
$\{\ket{00}, \ket{01}, \ket{10}, \ket{11}\}$
- This is why it is hard to simulate quantum algorithms because the space scales exponentially

## Example: 
2 different particles and I want to apply two different operators $A$ and $B$  to each particle
$$(A\ket{\psi} )\otimes (B\ket{\mu} )$$
## Example:
Computing inner product with the [[Bases| bell basis]]
$$\ket{\psi} =\frac{1}{\sqrt{ 2 }}\ket{+} \otimes \ket{+} + \frac{1}{\sqrt{ 2 }}\ket{-} \otimes \ket{-} $$

**Find:** $\braket{\Psi^+ | \Psi^+}$
$$\begin{align}
\left( \frac{1}{\sqrt{ 2 }}\bra{0} \otimes \bra{0} +\frac{1}{\sqrt{ 2 }}\bra{1} \otimes \bra{1} \right)\left(\frac{1}{\sqrt{ 2 }} \ket{0}  \otimes \ket{0} +\frac{1}{\sqrt{ 2 }} \ket{1} \otimes \ket{1} \right) \\

=\frac{1}{2}(\bra{0} \otimes \bra{0} )(\ket{0} \otimes \ket{0} )+ \frac{1}{2}(\bra{0} \otimes \bra{0} )(\ket{1} \otimes \ket{1} ) + \frac{1}{2}(\bra{1} \otimes \bra{1} )(\ket{0} \otimes \ket{0} )+\frac{1}{2}(\bra{1} \otimes \bra{1} )(\ket{1} \otimes \ket{1} ) \\
=\frac{1}{2}1*1+\frac{1}{2}0*0+0+\frac{1}{2}
\end{align}$$
**Find:** $\braket{\Psi^+ | \Psi^-} = 0$

**Find:** $\braket{\Psi^+ | \psi}$
$$\begin{align}
\left(\frac{1}{\sqrt{ 2 }}\bra{0} \otimes \bra{0} +\frac{1}{\sqrt{ 2 }} \bra{1} \otimes \bra{1} \right)\left(\frac{1}{\sqrt{ 2 }}\ket{+} \otimes \ket{+} + \frac{1}{\sqrt{ 2 }}\ket{-} \otimes \ket{-}\right) \\
=\left( \frac{1}{2}\braket{0 | + } \otimes \braket{0 | +} \right)+\frac{1}{2}\braket{00 | --} +\frac{1}{2}\braket{11 | ++} +\frac{1}{2}\braket{11 | --} \\ \\
=\frac{1}{2}\left( \frac{1}{\sqrt{ 2 }}  \frac{1}{\sqrt{ 2 }}\right)+\frac{1}{2}\left( \frac{1}{\sqrt{ 2 }} \frac{1}{\sqrt{ 2 }} \right)+\frac{1}{2}\left( \frac{1}{\sqrt{ 2 }} \frac{1}{\sqrt{ 2 }} \right) +\frac{1}{2}\left( -\frac{1}{\sqrt{ 2 }} * -\frac{1}{\sqrt{ 2 }} \right)
=1
\end{align}$$
