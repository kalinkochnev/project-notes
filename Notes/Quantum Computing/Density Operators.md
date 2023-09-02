- A quantum system can be prepared with predetermined propabilities $(p_{i}, \ket{\psi_{i}} )$ for $i=1$ to $i=n$
- The density operator is defined as $\rho=\sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}}$
- Not typically used for algorithms, but communication

**Probability and eigenvalues**
- This is an extension of the spectral decomp of an operator such that $\sum_{i}\lambda_{i}\ket{v_{i}}\bra{v_{i}}; \lambda_{i}\geq 0$
	- $p_{i}$ are the eigenvalues of the density operator

- Density operators unaffected by global phase

## Requirements
1. Must be Hermitian $\rho^{*}=\rho$
2. Positive semidefinite $\braket{x|\rho | x}\geq 0$
3. Has unit trace $tr(\rho)=1$ (sum of eigenvalues = 1)

- At least one ensemble of states exists to create each density operator $\rho$


# Partial trace
- Is linear
- Is equivalent to zooming in to a single party's particle to see what information is available to them

- Trace of outer product is same as inner product
- $tr_{A}$ ignores A's information. Only gives the reality that B can observe
$$
\begin{align}
\rho_{B}=tr_{A}(\ket{a_{1}} \bra{a_{2}} \otimes \ket{b_{1}} \bra{b_{2}} )=tr_{A}(\ket{a_{1}} \bra{a_{2}} )\otimes \ket{b_{1}} \bra{b_{2}}  \\
=\braket{a_{1} | a_{2} }\ket{b_{1}} \bra{b_{2}} 
\end{align}
$$
**any operator can be written as $\rho=\sum \ket{a_{1,i}}\bra{a_{2,i}}\otimes \ket{b_{1,i}}\bra{b_{2,i}}$

# Postulates
1. Open systems w/ incomplete information/uncertainty of state can be made with the density operator
2. Given $\rho$ and $U$, the evolved state is $U\rho U^{*}$
3. Given $\rho$ and $\{ M_{x} \}$, $p(x)=tr(M_{x}^{*}M_{x}\rho)$

# Examples
**What is the prob of measuring $\ket{\psi}$** with the ensembled $(1,\ket{\psi}\bra{\psi})$?
- Should be 1 since closed systems can still be created
- $M_{x}=\ket{0}\bra{0}$, $\rho=\ket{\psi}\bra{\psi}$
$$
\begin{align}
p(x)=tr(M_{x}^{*}M_{x}\rho) \\
=tr(\ket{0}\braket{0 | 0} \bra{0} (\ket{\psi} \bra{\psi} )) \\
=tr(\ket{0} \bra{0} )
\end{align}
$$
$\bra{\psi}(\ket{0}\braket{0 | 0} \bra{0})\ket{\psi}=\braket{\psi | 0}\braket{0 | \psi}=|\braket{\psi | 0}|^{2}$
