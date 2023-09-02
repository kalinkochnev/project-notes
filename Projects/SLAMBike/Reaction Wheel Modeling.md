# Hardware
- 24V DC motors
- Two relative encoders, one for arm and one for disk
	- Relative encoders are attached to fixed stator while measure the moveable rotor
	- Need to be initialized to 0 position at start
![[Pasted image 20230529150143.png]]


# Motion
![[Pasted image 20230529161633.png]]
- 2 DOF (angle of pend., angle of rotor)

- Potential energy is not affected by rotor position since it is distributed symmetrically across axis of rotation
- Torque of a motor (minus friction and electrodynamics specifics)
$$\tau=kI \text{ (k is a torque constant)}$$
- Torque of motor $\tau$ causes $-\tau$ torque on pendulum because of [[6-21-23#Notes| Newton's Third Law]]. The arm/rotor 

## Assumptions
- **Assume elasticity of motor shaft or pendulum link is negligible** cause this would effect potential energy
- Friction is ignored

# 2.5 Drive amplifier
- Let $u$ be the variable we control through the computer. 
- Let $10u=kI_{max}$ (max possible current supplied)
- 