**make sure to understand the properties of [[Skew Symmetric Matrices]]**

- The angular velocity ($\omega =\dot{\theta}$) is the same for all points on a body
	- Angular velocity is a quantity that can be addeed 

- Linear velocity depend on position on the body $\vec{v}=\vec{\omega } \times \vec{r}$

# Why can you add angular velocities together?
https://physics.stackexchange.com/questions/583504/is-direction-of-angular-velocity-just-a-definition-or-has-a-physical-significanc
https://physics.stackexchange.com/questions/596909/what-is-angular-velocity-in-3-dimensional-space-revised
https://physics.stackexchange.com/a/676499
https://www.youtube.com/shorts/0HFO8oHqOLc
https://math.stackexchange.com/questions/3541/how-can-angular-velocity-or-angular-momentum-be-a-vector
I don't have a good answer for this...

According to the textbook, angular velocities can be added together as free vectors provided they are relative to a common coordinate frame

# Derivative of a rotation matrix
$$
SR(\theta)=\frac{d}{d \theta} R(\theta)
$$

## Derivatives around single axis
$$
\begin{align}
\frac{d}{d \theta} R_{x, \theta} = S(i)R_{x, \theta} \\
\frac{d}{d \theta} R_{y, \theta} = S(i)R_{j, \theta} \\
\frac{d}{d \theta} R_{z, \theta} = S(i)R_{k, \theta}
\end{align}
$$

# Addition of Angular velocities
**Def**: Let $\omega_{ab}^{i}$ = the time derivative of the rotation matrix $R_{b}^{a}$ (angular velocity of frame j relative to frame i) with respect to frame $i$

## Big picture
==Angular velocities can be added together when they are expressed in the same coordinate frame!==
The total angular velocity w.r.t fixed frame is the combined angular velocities of each rotating frame but seen from the fixed frame 

$$
\begin{align}
R_{n}^{0}&=R_{1}^{0}\dots R_{n}^{n-1} \\
\dot{R}_{n}^{0}&= S(\omega_{0, n}^{0}) R_{n}^{n} \\
w_{0, n}^{0} &= w_{0, 1}^{0}+R_{1}^{0}w_{1, 2}^{1} + \dots +R_{n-1}^{0}w_{n-1,n}^{n -1}
\end{align}
$$


## Derivation
- Derive composition of angular velocities of moving frame $o_{1}$ and $o_{2}$ relative to fixed $o_{0}$
- **Assume that the 3 frames share a common origin!!!!**
- Let relative orientation be $R_{1}^{0}(t)$ and $R_{2}^{1}(t)$
$$
\begin{align}
R_{2}^{0}(t)&= R_{1}^{0}(t) R_{2}^{1}(t) \\
\implies\dot{R}_{2}^{0}(t) &= S(\omega_{0,2}^{0} )R_{2}^{0}  \\
&=\dot{R}_{1}^{0}(t) R_{2}^{1}(t) + R_{1}^{0}(t) \dot{R}_{2}^{1}(t) \\
&=S(w_{0,1}^{0})R_{1}^{0} R_{2}^{1} + R_{1}^{0}S(w_{1, 2}^{1})R_{2}^{1}  \\
\end{align}
$$
Insert $(R_{1}^{0})^{T} R_{1}^{0}$

By property 3 [[Skew Symmetric Matrices]]
$$
\begin{align}
&=S(w_{0,1}^{0})R_{2}^{0}+ R_{1}^{0}S(w_{1, 2}^{1}) (R_{1}^{0})^{T} R_{1}^{0}R_{2}^{1}  \\
&=S(w_{0,1}^{0})R_{2}^{0}+ S(R_{1}^{0} w_{1, 2}^{1}) R_{1}^{0}R_{2}^{1}  \\ \\
&= S(w_{0,1}^{0})R_{2}^{0}+ S(R_{1}^{0} w_{1, 2}^{1}) R_{2}^{0} \\
S(\omega_{0,2}^{0} )R_{2}^{0}&= \left[S(w_{0,1}^{0}) + S(R_{1}^{0} w_{1, 2}^{1})  \right]R_{2}^{0}
\end{align}
$$
Therefore 
$$
\omega_{0,2}^{0}= w_{0,1}^{0} + R_{1}^{0} w_{1, 2}^{1}
$$

# Linear velocity of a point attached to a moving frame
## Big picture
The combined linear velocity of a homogeneous transform has a component due to the rotation of the frame, as well as a translational component from the frames moving apart
$$
\begin{align}
\frac{d}{dt} p^{0} = \omega_{0, 1}^{0} \times p^{0}+v_{1}^{0}
\end{align}
$$

## Derivation
Let $p$ be a point fixed to $O_{1}$ that is moving (described by a homogeneous transform).
$$
H_{1}^{0}(t)=\begin{bmatrix}
R_{1}^{0}(t) & O_{1}^{0}(t) \\
0 & 1
\end{bmatrix}
$$

We want to find the relative velocity to the fixed frame $O_{0}$

$$
\begin{align}
p^{0}&=R_{1}^{0} p^{1} + O_{1}^{0}\\
\frac{d}{dt} p^{0} &= \dot{R}_{1}^{0}p^{1} + R_{1}^{0}\dot{p}^{1} + \dot{O}_{1}^{0} \\
\end{align}
$$
Since $p^{1}$ is fixed w.r.t frame 1, then $\dot{p}^{1}=0$
$$
\begin{align}
\frac{d}{dt} p^{0} &= \dot{R}_{1}^{0}p^{1} + \dot{O}_{1}^{0} \\
&=S(\omega_{0, 1}^{0})R_{1}^{0}p^{1} +v_{1}^{0} \\
&= \omega_{0, 1}^{0} \times p^{0}+v_{1}^{0}
\end{align}
$$
# Jacobian
Describes the velocities (translation and rotational velocity) of the end effector given the velocities of the prismatic/revolute joints.
$$
\begin{align}
v_{n}^{0}=J_{v}\dot{q} \\
\omega_{n}^{0}=J_{w}\dot{q}
\end{align}
$$
- Let $S(\omega_{0, n}^{0}) = \dot{R}_{n}^{0} (R_{n}^{0})^{T}$ define the angular velocity of the end effector and $v_{n}^{0}=\dot{O}_{n}^{0}$ define the linear velocity of the end-effector
## Manipulator jacobian (aka jacobian)
$$
\xi = J \dot{q}
$$
where 
$$
\begin{align}
J=\begin{bmatrix}
J_{V} \\
J_{\omega }
\end{bmatrix} \\
\xi=\begin{bmatrix}
v_{n}^{0} \\
\omega _{n}^{0}
\end{bmatrix}
\end{align}
$$

$$
\begin{align}
&J_{V}=[J_{V_1} \dots J_{V_{n}}] \\
&J_{V_{i}} = \begin{cases}
z_{i-1} \times (O_{i} - O_{i-1}) & \text{ for revolute} \\
z_{i-1} & \text{for prismatic}
\end{cases}
\end{align}
$$
$$
\begin{align}
&J_{\omega} = [J_{w_{1}} \dots J_{w_{n}}] \\
&J_{\omega_{i}} = \begin{cases}
z_{i-1} & \text{for revolute} \\
0 & \text{for prismatic}
\end{cases}
\end{align}
$$

We don't need to include $\dot{q}_{i}$ since we compute $J \dot{q}$ (the matrix multiplication) which distributes the term appropriately

## Angular velocity derivation

#### Big idea
This is the easier case. Prismatic joints do not affect the total angular velocity of the system. So total angular velocity only comes from the revolute.

$$
\omega_{n}^{0}=\sum_{i=1}^{n}\rho_{i} \dot{q}_{i} z_{i-1}^{0}
$$
Angular velocity vector of a frame is decided to be $z$ axis of the particular frame (with magnitude equal to $\omega$)
#### Derivation
- Can add angular velocities if in same coordinate frame
- Let $\omega_{i}^{i-1}$ be velocity of link $i$ relative to frame $O_{i-1}$ (the coordinate frame that is attached to the revolute joint)

**If revolute joint**
$q_{i}=\theta_{i}$ and the axis of rotation is $z_{i-1}$ 
$$
\omega_{i}^{i-1} = \dot{q}_{i} z_{i-1}^{i-1} = \dot{q}_{i}k
$$
**If a prismatic joint**
$\omega_{i}^{i-1}=0$ since prismatic joints don't rotate no angular velocity

Therefore the total angular velocity depends only on the prismatic joints. Define a dummy variable $\rho_{i}$ that = 1 if revolute and 0 if prismatic
$$
\omega_{n}^{0}=\sum_{i=1}^{n}\rho_{i} \dot{q}_{i} z_{i-1}^{0}
$$
Note: $z_{i-1}^{0}=R_{i-1}^{0}k$

**Therefore**: 
$$
J_{\omega}=[\rho_{1} z_{0} \dots \rho_{n} z_{n-1}]
$$



## Linear velocity
The linear velocity is the total derivative of $\dot{O}_{n}^{0}$, i.e. the contributions of the velocity from each joint (assuming all the other joints are held fixed). Also have to account for how the joint velocity changes over time

$$
\dot{O}_{n}^{0}=\sum_{i=1}^{n} \frac{\partial O_{n}^{0}}{\partial q_{i}} \frac{\partial q_{i}}{ \partial t}
$$

**$i$-th column of $J_{v}$**
$$
J_{v_{i}} = \frac{\partial O_{n}^{0}}{\partial q_{i}}
$$
### Case 1: prismatic joint
- direction of translation is parallel to $z_{i-1}$
- Magnitude of translation is $\dot{d}_{i}$

**Therefore** $\dot{O}_{n}^{0} = \dot{d}_{i} z_{i-1}^{0}$

### Case 2: revolute joints
- We fix all other joints except joint $i$
- The linear velocity is simply angular velocity of joint i  $(\dot{\theta}_{i} z_{i-1})$  crossed with the moment arm $(O_{i}-O_{i-1})$
$$
J_{v_{i}}=z_{i-1} \times (O_{n} - O_{i-1})
$$
![[Pasted image 20240430170100.png]]