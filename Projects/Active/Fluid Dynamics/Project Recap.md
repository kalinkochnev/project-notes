# Direct numerical simulation
- Simulate complex initial conditions for $\hat{\rho}, \hat{u}, \hat{v}, \hat{w}$ with $a+bi$. Uniformally randomly distributed
- 5/18/24 - Discovered mistake in $B_u$ Radoko is missing term from eq. (6) [[Instabilities of a time-dependent shear flow]]. Can set $A_U = 0$ to get similar results as Radko.
![[Pasted image 20240822145518.png]]
![[Pasted image 20240822161727.png]]
![[radkoderiv.png]]

- 5/31/24 - We switched to [[Thermohaline layering in dynamically and diffusively stable shear flows]] and reproduced figure 2
![[Pasted image 20240822163753.png]]

- 5/31/24 - Reproduced figure 1a [[Thermohaline layering in dynamically and diffusively stable shear flows]] using ode45
![[Pasted image 20240531120207.png]]
# Convex Optimization
- 4/12/24 - Initially used a time-independent P matrix but had bad results (Figure 2 of [[Instabilities of a time-dependent shear flow]])

![[Pasted image 20240822141901.png]]

- 4/21/24 - Time-dependent P'(t) matrix. Uses finite difference method to approximate derivative. We only need to integrate over one period of the system!!
- 4/24/24 - Yalmip solver can fail to solve depending on hyperparameters. 
	1. Increase the accuracy of bisection parameter to $\text{absgaptol =}1 \cdot 10^{-12}$. 
	2. Solve for $\lambda=0$ since it is trivial to check first.
	3. Enforce that M (the system matrix) is exactly periodic
![[Pasted image 20240822144854.png]]![[Lyapunov_Results.png]]
![[Pasted image 20240822145003.png]]
