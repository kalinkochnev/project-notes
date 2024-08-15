**System** - Device that transforms one signal to another



# Signal Operations
**Addition**: "stacking" the two signals together
**Multiplication**: 

## Time shift
$f(t-T)$ shifts signal to the right when $t>0$ Introduces a time delay of T. 
- you must substitute $(t-T)$ for all instances of $t$ to do the op
## Time scale
$f(\alpha t)$
- When $\alpha>0$ the signal is "shrunk"/sped up relative to $t=0$
- When $\alpha<0$ the signal is expanded/slowed downed relative to $t=0$

- you must substitute $\alpha t$ for all instances of $t$ to do the op
## Combination
Given $f(t)$ you can find $f(at-b)$ by

**option 1:**
1) Time shift by b (substitute $t-b$)
2) Time scale by a (substitute $\alpha t$)
$$
f(t) \to f((t-b)) \to f((at)-b)
$$
**option 2:**
1) Time scale by $a$ (sub $at$)
2) Time shift by $\frac{b}{a}$ (sub $t-\frac{b}{a}$)
$$
f(t) \to f(at) \to f\left( a\left( t-\frac{b}{a} \right) \right) \to f(at-b)
$$
# Building Block Signals
## Unit step
![[Pasted image 20240529101739.png]]
$$
f(t)=\begin{cases}
1 & t\geq 0 \\
0 & t<0
\end{cases}
$$

- You can create a "window" function by subtracting two step functions that are shifted
ex: $u(t)-u(t-3)$ is $1$ between $[0, 3)$
![[Pasted image 20240529101932.png]]

- You can create a window of a function in a certain interval like this
$$
f(x)[u(t)-u(t-3)]
$$
![[Pasted image 20240529102136.png]]

## Unit impulse 
![[Pasted image 20240529102410.png]]
$$
f(t)=\begin{cases}
1 & t=0 \\
0 & t\neq 0
\end{cases}
$$
- The arrow indicates the area under $\delta(t)$ (by default is 1)
$$
\int _{-\infty}^{\infty} \delta(t) \, dt=1 
$$
- Integral up to a value $t$ is the same as the unit step function!
$$
\int _{-\infty}^{t} \delta(t) \, dt = \begin{cases}
1 & t\geq 0 \\
0 & t<0
\end{cases} = \text{unit step! } u(t) 
$$
### Sampling property
- You can sample a signal at a certain point using a unit impulse signal
$$
\int _{-\infty}^{\infty} f(t)\delta(t-3) \, dx = f(3) 
$$

### Delta train
![[Pasted image 20240529103141.png]]
- Can create a correspondence between analog and digital signals by sampling at equally spaced points with multiple delta functions

$$
\delta_{T}(t)=\sum_{n=-\infty}^{\infty} f(t) \delta(t-nT)
$$
ex: Sample signal every 3 units $e^x \delta_{3}(t)$

## Exponential signal
$e^{a t}$ and $a=\sigma+j \omega$ 


### Case 1: Only real $\omega=0$
![[Pasted image 20240529103951.png]]
### Case 2: Only imaginary $a=0$
$$
e^{j\omega t} = \cos(\omega t)+j\sin(\omega t)
$$
![[Pasted image 20240529104117.png]]

### Case 3: Mixed $\omega\neq 0, \sigma\neq 0$
![[Pasted image 20240529104213.png]]


# Types of Systems
**System** device that transforms one signal to another

## Static vs dynamic
**Static**: Output signal only depends on the current input at that time
**Dynamic**: Output signal may depend on past or future input values

## Causal vs non-causal
**Causal** - output only depends on the past and/or present input
**Non-causal** - output may depend on future time and input values

ex: human speech is non-causal since what you say now depends on what you will say 5 seconds later

## Linear vs non-linear
**Linear** - linearity is preserved $au_{1} + bu_{2} \to a o_{1} + b o_{2}$ for **all inputs** (single counter example is enough)
=> if a system saturates then definitely not linear

ex: kitchen scale is non-linear since there is a saturation limit

## Time invariant vs time-varying
**Time invariant** - output does not depend on what time you input
- If $\forall T, f(t)\to y(t) == f(t-T)\to y(t -T)$ then it is time invariant 

ex: kitchen scale is time invariant, traffic is time varying

# LTI Systems
## How to determine if a system is linear/time-invariant
Let input = $f(t)$ and output $y(t)$
### Shortcut method
1) All terms that include $f, y$ are linear

ex: 
$\frac{d^{2}y}{dt^{2}} + 5 \frac{dy}{dt} + 6y(t)=4 \frac{df}{dt}+f(t)$ is **linear time invariant**
$\frac{d^{2}y}{dt^{2}} + \sin(t) \frac{dy}{dt} + 6[y(t)]^{2}=4 \frac{df}{dt}+f(t)$ is **non-linear** and **time varying**
$\frac{d^{2}y}{dt^{2}} + t^{2} \frac{dy}{dt} + 6t y(t)= 4 \frac{df}{dt}f(t) + f(t)$ has time varying terms ($t, t^{2}$) and non-linear terms ($\frac{df}{dt}f(t)$)

### Definition method
Apply definition of linearity and time invariance

#### Ex: Show that system is linear $\frac{dy}{dt}+t^{2}y(t)=(2t+3)f(t)$
1) If linear $f \to k_{1} f$, response (y) should be $k_{1}y$. Start with RHS and sub in $k_{1} f$ for f. Sub
$$
\begin{align} \\
(2t+3)f(t) \\ \\
k_{1}f [2t+3] = k_{1}\left[ \frac{dy}{dt}+t^{2}y \right]\\
k_{1}2t+3(k_{1}f) = \frac{d(k_{1}y)}{dt} + t^{2}(k_{1}y) \\
\text{output has form } k_{1}y
\end{align}
$$

2) If linear, an input $f\to f_{1}+f_{2}$ should result in $y_{1}+y_{2}$
$$
\begin{align}
(2t+3)f = \frac{dy}{dt}+t^{2}y\\

(2t+3)(f_{1}+f_{2}) = [\text{response 1}] + [\text{response 2}] \\  \\

(2t+3)(f_{1}+f_{2}) = [\frac{dy_{1}}{dt}+t^{2}y_{1}] + [\frac{dy_{2}}{dt}+t^{2}y_{2}] \\ 
(2t+3)(f_{1}+f_{2}) = \frac{d (y_{1} + y_{2})}{dt}+t^{2}(y_{1}+y_{2}) 

\end{align}
$$

#### Ex: show that system is non-linear
1) Substitute $f\to kf$ into RHS. Then use the LHS to show the response. It is linear if the response has $y\to ky$, but in this case we have $\sqrt{ k }y$
$$
\begin{align}
2f(t) = \frac{dy}{dt}+(y(t))^{2} \\
2(kf) = k [\frac{dy}{dt}+(y(t))^{2}]  \\
= \frac{d(yk)}{dt}+(\sqrt{ k }y)^{2}
\end{align}
$$

# Response of LTI systems
![[Pasted image 20240529204704.png]]
- Response of LTI is dependent on external input and the initial conditions prior to start of input
- Because LTI the response is a result of a combination of different effects
1) Response of no input $f(t)=0$ => response is solely a result of initial conditions
2) Response of  initial conditions = 0 => response is solely a result of input
3) Response of external input + non-zero initial conditions => a superposition of (1) and (2)

$$
\text{Total response} = \text{Zero input response } f(t)=0 + \text{zero state response } y(0^{-}) = \dot{y}(0^{-1})=\dots=0
$$ 
$$

$$

#### Ex: Consider LTI system in the table 
![[Pasted image 20240529205111.png]]
What is the system response when $f(t)=3u(t)$ and $y(0^{-})=1, \dot{y}(0^{-})=3$

Process: Lets say we have a specific system (input and initial conditions) that we want to know the response of. And we already know how the system responds based on some other information (like the table)
1) Assume we can find $y_{1}, y_{2}, y_{3}$ which are the responses of the system with only a single contributing effect, such as only input, only $y(0^{-1})$, and only $\dot{y}(0^{-1})$
2) Describe the total response $y(t)$ as a linear combination of $y_{1}, y_{2}, y_{3}$
3) Describe the response for the last column as a linear combination of $y_{1}, y_{2}, y_{3}$
4) Solve for $y_{1}, y_{2}, y_{3}$
5) Substitute $y_{1}, y_{2}, y_{3}$ back to get the total response $y(t)$
![[IMG_1021.png]]
