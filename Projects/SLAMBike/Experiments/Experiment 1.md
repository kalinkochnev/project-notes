# Page 21
- No control torque
$$
\begin{align}
\ddot{\theta}+\frac{mgl}{J}\sin \theta=0 \\
\ddot{\theta_{r}}=0
\end{align}
$$
- Initialize pendulum at 20deg and measure pendulum and rotor angles.
- For small angles, the frequency should be $\omega _p=\sqrt{ \frac{mgl}{J} }$
- If no change in position and no velocity for motor, then $\ddot{\theta _{r}}=0$
- In our model we said that $\theta=$ axle encoder, and $\theta_{r}=\theta+$flywheel encoder measurements
- Because of friction, the motor does not rotate while the pendulum arm spins, so $\theta_{r}=\theta+0$

- Friction has a significant effect and needs to be accounted for, especially in the rotor
- The friction in the pendulum is negligible (can be verified). Time constant of up to a minute (according to the book)