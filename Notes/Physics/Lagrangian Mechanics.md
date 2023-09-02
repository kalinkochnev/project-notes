https://www.youtube.com/watch?v=8UtnDaGHpq0
### Useful when
- Forces are constrained
- Generalized coordinates
- Need to describe a system based on degrees of freedom (# DOF = # lagrange equations)
- If overconstrained

# Lagrangian
$L=T-U$ where
- T is kinetic energy $=\frac{1}{2}m(\dot{x}^{2}+\dot{y}^{2}+\dot{z}^{2})$
- U is potential which can depend on position and time $=U(x,y,z,t)$
- A function of generalized coordinates $(q_{1}\dots q_{n})$ and their derivatives $(\dot{q_{1}}\dots  \dot{q_{n}})$
  $$L(q_{1},\dots,q_{n}, \dot{q_{1}},\dots, \dot{q_{n}})$$

https://en.wikipedia.org/wiki/Stationary-action_principle
- Action ($S$) is defined as the integral of the Lagrangian between two moments in time
- Let $q=(x,y,z, \dots)$ represent the coordinates of the system
- $S=\int _{t_{1}}^{t_{2}}L(q(t), \dot{q}(t), t) \, dt$
![[Least_action_principle.svg]]
## Principle of least action
http://www.scholarpedia.org/article/Principle_of_least_action
Imagine generating all possible paths a system can take from point A to point B. The path that will be taken is the one that ensures that the change in action is stationary, doesn't change $\partial S=0$

## Process (non-conservative forces)
1. Pick coordinates
2. Find kinetic and potential energy to find $L$
3. Apply the [[Calculus of Variations#Euler-Lagrange Equation|Euler-Lagrange Equation]] on $L$
4. Profit

# Non-conservative forces
https://phys.libretexts.org/Bookshelves/Classical_Mechanics/Classical_Mechanics_(Tatum)/13%3A_Lagrangian_Mechanics/13.04%3A_The_Lagrangian_Equations_of_Motion#:~:text=Pj%3Dddt,with%20a%20given%20generalized%20coordinate.

For set of generalized coordinates $q_{1},\dots,q_{n}$, where $k=1,\dots,n$
$$
\frac{d}{dt}\left( \frac{\partial L}{\partial \dot{q_{k}}}  \right) - \frac{\partial L}{\partial q_{k}}=\tau_{k}
$$
- $\tau_{k}$ are the generalized forces/torques in the $q_{k}$ direction
- This is when there may be non-conservative forces [[Advanced_Physics_Nick_Lucid_Jan_2023.pdf#page=85|Advanced physics Textbook]]

**Virtual displacement:** a small (not real) change from one geometrically admissible state to a nearby geometrically admissible state

**Generalized coordinates:** Minimal, complete (describes all configurations at all times) and independent (if all coordinates fixed except one, there is a continuous set of values the one can take on)
ex: describing a pendulum position (x,y) using ($\theta$) relative to vertical

- Choice of independent coordinates can simplify equations of motion
- But also coordinates can be dependent as long as there is a constraint equation