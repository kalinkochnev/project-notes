# Modeling systems using state space repr.


> [!PDF|yellow] [[Control System Engineering.pdf#page=134&selection=67,4,68,22&color=yellow|Control System Engineering, p.96]]
> > time-domain approach can also be used for the same class of systems modeled by the classical approach

**Approach**
1. **State variable selection**: a subset of all possible system variables and call the variables in this subset state variables (all other values can be solved using these variables)
2. **State equations:** an nth-order system, write n simultaneous, first-order ODEs in terms of the state variables
3. If we know the initial condition of all of the state variables at $t_{0}$ as well as the system input for $t\geq t_{0}$ , we can solve the simultaneous differential equations for the state variables for $t\geq t_{0}$. 
4. **Output equation:** the state variables with the system’s input and find all of the other system variables for $t\geq t_{0}$.

Example of (4):
> [!PDF|yellow] [[Control System Engineering.pdf#page=142&selection=62,29,101,35&color=yellow|Control System Engineering, p.104]]
> > choose the state variables as the quantities that are differentiated, namely v C and i L. Using Eq. (3.20) as a guide, we see that the state-space representation is complete if the right-hand sides of Eqs. (3.22) and (3.23) can be written as linear combinations of the state variables and the input. Since i C and v L are not state variables, our next step is to express iC and v L as linear combinations of the state variables


> [!PDF|yellow] [[Control System Engineering.pdf#page=137&selection=296,62,298,8&color=yellow|Control System Engineering, p.99]]
> > Typically, the minimum number of state variables required to describe a system equals the order of the differential equation

> [!PDF|yellow] [[Control System Engineering.pdf#page=138&selection=2,55,3,45&color=yellow|Control System Engineering, p.100]]
> > within this minimal set the state variables must be linearly independent.

> [!PDF|yellow] [[Control System Engineering.pdf#page=138&selection=142,79,144,34&color=yellow|Control System Engineering, p.100]]
> >  state-space representation is not unique, since a different choice of state variables leads to a different representation of the same system.

![[Control System Engineering.pdf#page=139&rect=86,138,457,345&color=yellow|Control System Engineering, p.101]]

> [!PDF|yellow] [[Control System Engineering.pdf#page=141&selection=14,78,20,31&color=yellow|Control System Engineering, p.103]]
> > Cases arise where these variables, although linearly independent, are also decoupled. That is, some linearly independent variables are not required in order to solve for any of the other linearly independent variables 

- Example: We only need one variable in order to solve for a mass and a viscous damper b/c it is a first order equation.
$$
M \frac{dv}{dt} + Dv = f(t)
$$ 
- However we might want to determine the position over time, so we add an integrator.
![[Control System Engineering.pdf#page=141&rect=415,331,583,419&color=yellow|Control System Engineering, p.103]]


# Converting Transfer Function to State Space
> [!PDF|yellow] [[Control System Engineering.pdf#page=148&selection=11,0,20,55&color=yellow|Control System Engineering, p.110]]
> > At first we select a set of state variables, called phase variables, where each subsequent state variable is defined to be the derivative of the previous state variable



> [!PDF|yellow] [[Control System Engineering.pdf#page=149&selection=257,18,263,96&color=yellow|Control System Engineering, p.111]]
> > to convert a transfer function into state equations in phase-variable form, we first convert the transfer function to a differential equation by cross-multiplying and taking the inverse Laplace transform, assuming zero initial conditions. Then we represent the differential equation in state space in phase-variable form. An example illustrates the process.
> 
> 

> [!PDF|yellow] [[Control System Engineering.pdf#page=151&selection=0,75,9,19&color=yellow|Control System Engineering, p.113]]
> > If a transfer function has a polynomial in s in the numerator that is of order less than the polynomial in the denominator ... the numerator and denominator can be handled separately.
> 

