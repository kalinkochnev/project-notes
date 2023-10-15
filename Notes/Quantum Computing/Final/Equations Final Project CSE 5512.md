$\ket{\psi}$
$$i\hbar \frac{\partial}{\partial t}\ket{\psi(t)}=\hat{H}\ket{\psi(t)}$$
$$\hat{H}=\hat{T}+\hat{V}$$
$$\hat{H}=\sum_{\psi \in \text{energy levels}} E_{\psi} \ket{\psi} \bra{\psi}  $$
$$\hat{H}\ket{\Psi} =E_{\Psi}\ket{\Psi} \text{ where } E_{\psi} \text{ is the energy for observable } \ket{\Psi}$$
$\ket{\Psi}=\ket{\psi_{1}}+\ket{\psi_{2}}$
$$\hat{H}\ket{\Psi}=\hat{H}\ket{\psi_{1}}+\hat{H}\ket{\psi_{2}}=\text{ total energy}$$
$$i\hbar \frac{\partial}{\partial t}\ket{\psi(t)}=\hat{H}\ket{\psi(t)}$$
$$\begin{align*}
i\hbar \frac{\partial}{\partial t}\ket{\Psi}& = \hat{H}\ket{\Psi}  \\
\frac{\partial}{\partial t}\ket{\Psi}& = \frac{1}{i\hbar} E_{\Psi}\ket{\Psi} \\
\frac{\partial}{\partial t}\ket{\Psi} &= -\frac{i}{\hbar} E_{\Psi}\ket{\Psi} \\
\ket{\Psi(t)} &=e^{-iE_{\psi}t/\hbar}\ket{\Psi(0)}
\end{align*}$$
$$\begin{align*}
P(x)&=\braket{\Psi(x,t) | \Psi(x,t)}=\ket{\Psi(x,t)}\ket{\Psi(x,t)}^{*} \\
&= (e^{-iE_{\psi}t/\hbar})(e^{iE_{\psi}t/\hbar})\braket{\Psi(x,0) | \Psi(x,0)} \\
&=\braket{\Psi(x,0) | \Psi(x,0)}
\end{align*}$$
$\hat{U}(t)=\exp({-\hat{i}Ht/\hbar})$

$\ket{E_{j}}_{L}$
$\ket{E_{j}}_{R}$

$$\ket{TFD}=\frac{1}{\sqrt{ Tr(e^{-\beta H}) }} \sum_{j \in \text{energy levels}}e^{-\beta E_{j}/2}\ket{E_{j}}_{L}\otimes  \bar{\ket{E_{j}}_{R}}$$

$\rho=e^{-\beta H}$
$\rho_{L}=tr_{R}(\ket{TFD}\bra{TFD})$
$\exp(i \hat{H}_{L}t_{L})$.
