- Accurate mathematical model of system is most important step
- Assume causality: $t_{i} \implies t_{i+1}$

# Types of systems
**Linear system** - the principle of superposition holds.
$$
\begin{align}
F(x_{1}+ x_{2}) &= F(x_{1}) + F(x_{2}) \ \\
F(\alpha x) &= \alpha F(x)
\end{align}
$$
- Response to several inputs can be treated by adding one input's response at a time

- **Time invariant** systems can be described with ODEs that don't depend on time
- **linear time-varying** systems depend on time

# Transfer functions and Impulse Response
**Transfer function of LTI** (linear time invariant) ODE is the ratio of output laplace (response function) and input laplace (driving function)

*initial conditions must be 0*

![[Pasted image 20231220175829.png]]
![[Pasted image 20231220180033.png]]

- Transfer func. is the ODE that relates the output variable to the input variable
- You must correct for units in transfer func
- Transfer func characterizes the whole dynamical system, can be found experimentally by using specific inputs to test response

### Convolution
$X(s), Y(s)$ are laplace transforms of input $x(t)$ and output $y(t)$

$$
\begin{gather}
\text{transfer func} = G(s) = \frac{Y(s)}{G(s)} \\

Y(s) = G(s)X(s)
\end{gather}
$$
- Output in freq domain as expressed by multiplication with transfer func and input signal in freq domain

- Multiplication equiv to convolution in time domain. Inverse laplace of $Y(s)$ is 
*$g(t)=x(t) =0 \text{ for } t<0$*
![[Pasted image 20231220180827.png]]

### Impulse response
Consider output to LTI system with an input of unit impulse/dirac delta function (with init conds of 0).
- ==would be nice to have proof at some point== dirac delta input is equivalent to identity element in frequency domain

$$
\begin{gather}
Y(s)=G(s) \delta(s)  \\
Y(s)=G(s)
\end{gather}
$$
So if we take the inverse laplace of time domain output after a unit impulse we can fully characterize the transfer function from it (assuming LTI)
$$
Y(s) = G(s) \implies \mathscr{L}^{-1}\{ y(t) \} = Y(s) = G(s) 
$$


# Block diagram notation
- A pictorial repr of function performed by components and flow of signals
- Functional blocks apply a mathematical operation to input and return it in output signal

**Branch point** - signal from block goes to other blogs or summing points concurrently
![[Pasted image 20231221172958.png]]
**Summing point** - cross symbol with (+) /(-) indicating adding or subtracting signal ![[Pasted image 20231221172926.png]]

---

# Common transfer functions
- The feedback transfer function $H(s)$ must scale the output units (lets say temperature) to the proper units for inputting back into controller (lets say voltage, position, or force)
![[Pasted image 20231221173355.png]]

## Open loop
- relates how the feedback changes depending on the error. ratio of feedback signal $B(s)$ to error signal $E(s)$
==I don't get get where the G(s)H(s) and G(s) come from
$$
\frac{B(s)}{E(s)}=G(s)H(s)
$$

## Feed forward
- relates output signal to error signal
$$
\frac{C(s)}{E(s)}= G(s)
$$
## Closed loop
- The transfer function for how the output and input are related for a closed loop controller are
- The 
*step 1*. output signal in terms of input, feedback and output
$$
\begin{align}
C(s) &=G(s)E(s)  \\
E(s) &= R(s) - B(s) \\
&=R(s) - H(s)C(s) \\ \\
C(s)&=G(s)\left[R(s)-H(s)C(s)\right] \\
\end{align}
$$
*step 2.* solve for $C(s)$ and find the ratio between output and input
$$
\begin{align}
C(s) + H(s)G(s)C(s) &= G(s)R(s) \\
C(s)[1+H(s)G(s)] &= G(s)R(s) \\
\frac{\text{output}}{\text{input}}=\frac{C(s)}{R(s)} &= \frac{G(s)}{1+H(s)G(s)}
\end{align}
$$
# Types of controls
![[Pasted image 20231221173355.png]]
## On/off control
- differential gap  is like tolerance to prevent too frequent switching from on to off
- Results in oscillation which can be reduced with smaller differential gap
![[Pasted image 20231221181435.png]]


## Proportional Control
- Essentially amplifies the error signal with adjustable gain $K_{p}$
$$
\begin{align}
u(t) = K_{p} e(t) \\
\text{or} \\
\frac{U(s)}{E(s)}=K_{p}
\end{align}

$$

## Integral Control
- The rate at which the output is changed depends on the current error (larger error = greater rate of change)
- output = $u(t)$, error = $e(t)$
$$
\begin{align}
\frac{du(t)}{dt}=K_{i}e(t) \\
u(t)=K_{i} \int _{0}^{t} e(t) \, dt 
\end{align}
$$
Laplace form:
$$
\frac{U(s)}{E(s)}=\frac{K_{i}}{s}
$$

## Proportional + Integral Control
- $T_{i}$ known as "integral time"
$$
u(t) = K_{p}e(t) + \frac{K_{p}}{T_{i}} \int _{0}^{t}e(t) \, dt 
$$
Laplace form:
$$
\frac{U(s)}{E(s)} = K_{p}\left( 1+\frac{1}{T_{i}s} \right)
$$

## Proportional + Derivative
- Change the output proportional to how quickly the error changes ()
$$
u(t) = K_{p}e(t) + K_{p}T_{d} \frac{de(t)}{dt}
$$
$$
\frac{U(s)}{E(s)} = K_{p}(1+T_{d}s)
$$
## PID
- $K_{p}$ proportional gain, $T_{i}$ integral time, $T_{d}$ derivative time
$$
u(t)=K_{p}e(t) + \frac{K_{p}}{T_{i}}\int _{0}^{t}e(t) \, dt + K_{p}T_{d} \frac{de(t)}{dt}
$$
$$
\frac{U(s)}{E(s)} = K_{P}\left( 1+\frac{1}{T_{i}s} + T_{d}s \right)
$$
![[Pasted image 20231221182917.png]]

# Drawing a block diagram
1. Write equation for dynamic behavior of components
2. Take laplace assuming 0 initial condition
3. Represent laplace in block form
4. Assemble element together



### Example: RLC Circuit
![[Pasted image 20231221185206.png]]
**Figure A**
-The current through circuit depends on voltage difference between $e_{i}$ and $e_{0}$
- The current through the capacitor depends on the total charge across capacitor and capacitor constant
$$
\begin{align}
i = \frac{e_{i}-e_{0}}{R}  \\
e_{0}=\frac{\left( \int i \, dt  \right)}{C}
\end{align}
$$
Assuming zero initial condition ==(no current, no voltage?)==, laplace
$$
\begin{align}
I(s) = \frac{E_{i}(s) - E_{0}(s)}{R} \\
E_{0}(s)=\frac{I(s)}{Cs}
\end{align}
$$

**Fig B**: $I(s)$ can be written as subtraction of input voltage and feedback voltage (with constant multiplier)
**Fig C:** Capacitor is a function of current and scalar multiplication
**Fig D:** current goes through resistor and then capacitor



## Simplifying block diagram
- Blocks can be in series if output of one block is not affected by next block
- 