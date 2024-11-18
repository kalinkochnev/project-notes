
# Improving steady state error via Cascade Compensation
> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=7,43,8,76&color=yellow|Control System Engineering, p.362]]
> > One objective of this design is to improve the steady-state error without appreciably affecting the transient response.

> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=10,0,17,35&color=yellow|Control System Engineering, p.362]]
> >  first technique is ideal integral compensation, which uses a pure integrator to place an open-loop, forward-path pole at the origin, thus increasing the system type and reducing the error to zero

> [!PDF|note] [[Control System Engineering.pdf#page=463&selection=17,41,20,11&color=note|Control System Engineering, p.362]]
> > second technique does not use pure integration. This compensation technique places the pole near the origin, and although it does not drive the steady-state error to zero, it does yield a measurable reduction in steadystate error


> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=77,0,78,32&color=yellow|Control System Engineering, p.362]]
> > Steady-state error can be improved by placing an open-loop pole at the origin, because this increases the system type by one

> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=92,2,103,24&color=yellow|Control System Engineering, p.362]]
> > If we add a pole at the origin to increase the system type, the angular contribution of the open-loop poles at point A is no longer 180°, and the root locus no longer goes through point A, as shown in Figure 9.3

> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=106,0,114,65&color=yellow|Control System Engineering, p.362]]
> > To solve the problem, we also add a zero close to the pole at the origin, as shown in Figure 9.3(c). Now the angular contribution of the compensator zero and compensator pole cancel out, point A is still on the root locus, and the system type has been increase
> 
> 

> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=117,8,117,92&color=yellow|Control System Engineering, p.362]]
> > improved the steady-state error without appreciably affecting the transient response


> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=69,6,73,61&color=yellow|Control System Engineering, p.362]]
> > we use the name lag compensator when the cascade compensator does not employ pure integration

> [!PDF|yellow] [[Control System Engineering.pdf#page=463&selection=58,52,60,15&color=yellow|Control System Engineering, p.362]]
> > second technique uses what we call a lag compensator

> [!PDF|yellow] [[Control System Engineering.pdf#page=464&selection=0,0,4,1&color=yellow|Control System Engineering, p.363]]
> > A compensator with a pole at the origin and a zero close to the pole is called an ideal integral compensator.

