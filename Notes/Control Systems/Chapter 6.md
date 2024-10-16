# Stability for LTIs
> [!PDF|yellow] [[Control System Engineering.pdf#page=311&selection=20,34,22,39&color=yellow|Control System Engineering, p.243]]
> > we can control the output of a system if the steadystate response consists of only the forced response. But the total response of a system is the sum of the forced and natural responses

> [!PDF|yellow] [[Control System Engineering.pdf#page=311&selection=41,10,48,5&color=yellow|Control System Engineering, p.243]]
> > time-invariant system is stable if the natural response approaches zero as time approaches infinity.

> [!PDF|yellow] [[Control System Engineering.pdf#page=311&selection=58,1,62,44&color=yellow|Control System Engineering, p.243]]
> > marginally stable if the natural response neither decays nor grows but remains constant or oscillates

> [!PDF|yellow] [[Control System Engineering.pdf#page=311&selection=51,0,56,4&color=yellow|Control System Engineering, p.243]]
> > unstable if the natural response grows without bound as time approaches infinity

> [!PDF|note] [[Control System Engineering.pdf#page=311&selection=75,19,83,4&color=note|Control System Engineering, p.243]]
> > we realize that if the input is bounded and the total response is not approaching infinity as time approaches infinity, then the natural response is obviously not approaching infinity

# Total response BIBO stability
> [!PDF|yellow] [[Control System Engineering.pdf#page=311&selection=98,0,102,37&color=yellow|Control System Engineering, p.243]]
> > A system is stable if every bounded input yields a bounded output

> [!PDF|yellow] [[Control System Engineering.pdf#page=311&selection=124,0,128,41&color=yellow|Control System Engineering, p.243]]
> > A system is unstable if any bounded input yields an unbounded output.

## LTI Marginally Stable is BIBO unstable
> [!PDF|yellow] [[Control System Engineering.pdf#page=312&selection=9,26,14,55&color=yellow|Control System Engineering, p.244]]
> >  if the natural response is undamped, a bounded sinusoidal input of the same frequency yields a natural response of growing oscillations. Hence, the system appears stable for all bounded inputs except this one sinusoid. Thus, marginally stable systems by the natural response definitions are included as unstable systems under the BIBO


> [!PDF|yellow] [[Control System Engineering.pdf#page=312&selection=111,74,124,0&color=yellow|Control System Engineering, p.244]]
> > poles of multiplicity greater than 1 on the imaginary axis lead to the sum of responses of the form $At^{n}\cos(\omega t + \phi)$


# Stability in practice
> [!PDF|yellow] [[Control System Engineering.pdf#page=313&selection=6,0,13,31&color=yellow|Control System Engineering, p.245]]
> > Unfortunately, a typical problem that arises is shown in Figure 6.2. Although we know the poles of the forward transfer function in Figure 6.2(a), we do not know the location of the poles of the equivalent closed-loop system of Figure 6.2(b) without factoring or otherwise solving for the roots


> [!PDF|yellow] [[Control System Engineering.pdf#page=313&selection=15,23,25,0&color=yellow|Control System Engineering, p.245]]
> > f the closed-loop transfer function has only left-half-plane poles, then the factors of the denominator of the closed-loop system transfer function consist of products of terms such as $s+a_{i}$

> [!PDF|important] [[Control System Engineering.pdf#page=313&selection=27,0,34,6&color=important|Control System Engineering, p.245]]
> > $a_{i}$ is real and positive, or complex with a positive real part. The product of such terms is a polynomial with all positive coefficients

**important**
> [!PDF|red] [[Control System Engineering.pdf#page=314&selection=0,0,10,60&color=red|Control System Engineering, p.246]]
> > sufficient condition for a system to be unstable is that all signs of the coefficients of the denominator of the closed-loop transfer function are not the same. If powers of s are missing, the system is either unstable or, at best, marginally stable
> 
> 

# Routh-Hurwitz Criterion
> [!PDF|yellow] [[Control System Engineering.pdf#page=314&selection=32,34,44,1&color=yellow|Control System Engineering, p.246]]
> > Using this method, we can tell how many closed-loop system poles are in the left half-plane, in the right half-plane, and on the jω-axis. (Notice that we say how many, not where.
> 
> 

> [!PDF|yellow] [[Control System Engineering.pdf#page=314&selection=80,14,85,14&color=yellow|Control System Engineering, p.246]]
> > The power of the method lies in design rather than analysis. For example, if you have an unknown parameter in the denominator of a transfer function, it is difficult to determine via a calculator the range of this parameter to yield stability
> 
> 

1) Generate a data table called a Routh table
2) interpret the Routh table to tell how many closed-loop system poles are in the left half-plane, the right half-plane, and on the jω-axis


