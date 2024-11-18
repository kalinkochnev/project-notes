# Highlights
> [!PDF|yellow] [[Control System Engineering.pdf#page=397&selection=40,18,46,44&color=yellow|Control System Engineering, p.306]]
> > gains and other system parameters were designed to yield a desired transient response for only first- and second-order systems. Even though the root locus can be used to solve the same kind of problem, its real power lies in its ability to provide solutions for systems of order higher than 2

> [!PDF|yellow] [[Control System Engineering.pdf#page=397&selection=70,63,76,1&color=yellow|Control System Engineering, p.306]]
> > poles of the closed-loop transfer function are more difficult to fin

> [!PDF|yellow] [[Control System Engineering.pdf#page=397&selection=80,36,81,11&color=yellow|Control System Engineering, p.306]]
> > further, the closed-loop poles change with changes in system gain

> [!PDF|yellow] [[Control System Engineering.pdf#page=398&selection=52,9,68,1&color=yellow|Control System Engineering, p.307]]
> > the zeros of T(s) consist of the zeros of G(s) and the poles of H(s)


> [!PDF|yellow] [[Control System Engineering.pdf#page=398&selection=189,1,204,1&color=yellow|Control System Engineering, p.307]]
> >  Since the system’s transient response and stability are dependent upon the poles of T(s), we have no knowledge of the system’s performance unless we factor the denominator for specific values of K

> [!PDF|yellow] [[Control System Engineering.pdf#page=398&selection=245,2,251,36&color=yellow|Control System Engineering, p.307]]
> > If the complex number is substituted into a complex function, F(s), another complex number will resul

> [!PDF|yellow] [[Control System Engineering.pdf#page=398&selection=312,16,342,1&color=yellow|Control System Engineering, p.307]]
> >  (s a) is a complex number and can be represented by a vector drawn from the zero of the function to the point s. For example, s 7 s®5 j2 is a complex number drawn from the zero of the function, 7, to the point s, which is 5 j2


> [!PDF|yellow] [[Control System Engineering.pdf#page=399&selection=19,0,20,30&color=yellow|Control System Engineering, p.308]]
> > Each factor in the numerator and each factor in the denominator is a complex number that can be represented as a vector

![[Control System Engineering.pdf#page=398&rect=162,63,379,117&color=yellow|Control System Engineering, p.307]]

> [!PDF|yellow] [[Control System Engineering.pdf#page=399&selection=31,2,43,0&color=yellow|Control System Engineering, p.308]]
> > Since each complex factor can be thought of as a vector, the magnitude, M, of F(s) at any point, s

![[Control System Engineering.pdf#page=399&rect=297,273,462,332&color=yellow|Control System Engineering, p.308]]

> [!PDF|yellow] [[Control System Engineering.pdf#page=399&selection=105,0,126,1&color=yellow|Control System Engineering, p.308]]
> >  s p j , is the magnitude of the vector drawn from the pole of F(s) at p j to the point s

![[Control System Engineering.pdf#page=399&rect=292,140,463,203&color=yellow|Control System Engineering, p.308]]

> [!PDF|yellow] [[Control System Engineering.pdf#page=399&selection=172,8,201,0&color=yellow|Control System Engineering, p.308]]
> > zero angle is the angle, measured from the positive extension of the real axis, of a vector drawn from the zero of F(s) at zi to the point s, and a pole angle is the angle, measured from the positive extension of the real axis, of the vector drawn from the pole of F(s) at p j to the point s

![[Control System Engineering.pdf#page=400&rect=94,326,568,656&color=yellow|Control System Engineering, p.309]]


- As K changes, the locations of the pole change
![[Control System Engineering.pdf#page=402&rect=95,270,560,712&color=yellow|Control System Engineering, p.311]]


> [!PDF|yellow] [[Control System Engineering.pdf#page=403&selection=15,58,21,62&color=yellow|Control System Engineering, p.312]]
> > From these properties we will be able to make a rapid sketch of the root locus for higher-order systems without having to factor the denominator of the closed-loop transfer function

- This is important in understanding what root locus really is
- We can find the zeros of a closed loop transfer function $T(s)=\frac{KG(s)}{1+KG(s)H(s)}$ by factoring solving when the denominator is 
$$
\begin{align}
1+KG(s)H(s)=0 \\
KG(s)H(s)=-1
\end{align}
$$
- Since substituting a complex value into $s$ can be represented as a vector, when the LHS = -1 is when the LHS vector is pointing at $180^o$ 
$$
\begin{align}
KG(s)H(s) = -1 \\
KG(s)H(s) = 1 \angle(2k+1)180^o \\ \text{ for } k=0, \pm 1, \pm 2, \dots
\end{align}
$$
- Also must satisfy the magnitude of $|KG(s)H(s)| = 1$, so let $K=\frac{1}{G(s)H(s)}$


> [!PDF|note] [[Control System Engineering.pdf#page=403&selection=101,29,124,1&color=note|Control System Engineering, p.312]]
> > if a value of s is substituted into the function KG(s)H(s), a complex number results. If the angle of the complex number is an odd multiple of 180°, that value of s is a system pole for some particular value of K
> 
> 

![[Control System Engineering.pdf#page=403&rect=299,295,569,375&color=yellow|Control System Engineering, p.312]]

## Example!
> [!PDF|yellow] [[Control System Engineering.pdf#page=404&selection=32,66,34,10&color=yellow|Control System Engineering, p.313]]
> > Let us apply the complex number concepts reviewed in Section 8.1 to the root locus of the system shown in Figure 8.6

> [!PDF|yellow] [[Control System Engineering.pdf#page=404&selection=87,0,99,35&color=yellow|Control System Engineering, p.313]]
> > If point s is a closed-loop system pole for some value of gain, K, then s must satisfy Eqs. (8.14) and (8.15)

> [!PDF|note] [[Control System Engineering.pdf#page=404&selection=106,20,108,0&color=note|Control System Engineering, p.313]]
> > then the angles of the zeros minus the angles of the poles must equal an odd multiple of 180

> [!PDF|yellow] [[Control System Engineering.pdf#page=404&selection=152,0,181,51&color=yellow|Control System Engineering, p.313]]
> > If these calculations are repeated for the point 2 j 2 2 , the angles do add up to 180°. That is, 2 j 2 2 is a point on the root locus for some value of gain

**Summary**
> [!PDF|important] [[Control System Engineering.pdf#page=405&selection=69,44,111,52&color=important|Control System Engineering, p.314]]
> > Given the poles and zeros of the open-loop transfer function, KG(s)H(s), a point in the s-plane is on the root locus for a particular value of gain, K, if the angles of the zeros minus the angles of the poles, all drawn to the selected point on the s-plane, add up to 2k 1 180°. Furthermore, gain K at that point for which the angles add up to 2k 1 180° is found by dividing the product of the pole lengths by the product of the zero lengths.

## Sketching rules
> [!PDF|yellow] [[Control System Engineering.pdf#page=406&selection=19,1,28,22&color=yellow|Control System Engineering, p.315]]
> > Each closed-loop pole moves as the gain is varied. If we define a branch as the path that one pole traverses, then there will be one branch for each closed-loop pole.

> [!PDF|yellow] [[Control System Engineering.pdf#page=406&selection=47,0,56,49&color=yellow|Control System Engineering, p.315]]
> > If complex closed-loop poles do not exist in conjugate pairs, the resulting polynomial, formed by multiplying the factors containing the closed-loop poles, would have complex coefficients. Physically realizable systems cannot have complex coefficients in their transfer functions. Thus, we conclude: The root locus is symmetrical about the real axis

> [!PDF|yellow] [[Control System Engineering.pdf#page=406&selection=67,31,88,47&color=yellow|Control System Engineering, p.315]]
> > If an attempt is made to calculate the angular contribution of the poles and zeros at each point, P1 , P2 , P3 , and P4 , along the real axis, we observe the following

> [!PDF|yellow] [[Control System Engineering.pdf#page=406&selection=88,67,90,4&color=yellow|Control System Engineering, p.315]]
> > the angular contribution of a pair of open-loop complex poles or zeros is zero

> [!PDF|yellow] [[Control System Engineering.pdf#page=406&selection=90,18,91,49&color=yellow|Control System Engineering, p.315]]
> > contribution of the open-loop poles and open-loop zeros to the left of the respective point is zero

> [!PDF|note] [[Control System Engineering.pdf#page=406&selection=92,0,93,78&color=note|Control System Engineering, p.315]]
> > only contribution to the angle at any of the points comes from the open-loop, real-axis poles and zeros that exist to the right of the respective

> [!PDF|yellow] [[Control System Engineering.pdf#page=406&selection=111,0,121,15&color=yellow|Control System Engineering, p.315]]
> > On the real axis, for K 0 the root locus exists to the left of an odd number of real-axis, finite open-loop poles and/or finite open-loop zeros

> [!PDF|yellow] [[Control System Engineering.pdf#page=406&selection=139,0,142,10&color=yellow|Control System Engineering, p.315]]
> > Where does the root locus begin (zero gain) and end (infinite gain)

> [!PDF|yellow] [[Control System Engineering.pdf#page=407&selection=43,16,63,34&color=yellow|Control System Engineering, p.316]]
> > we see that the closed-loop system poles at small gains approach the combined poles of G(s) and H(s). We conclude that the root locus begins at the poles of G(s)H(s), the open-loop transfer function

> [!PDF|yellow] [[Control System Engineering.pdf#page=407&selection=153,0,153,70&color=yellow|Control System Engineering, p.316]]
> > Remember that these poles and zeros are the open-loop poles and zeros.

> [!PDF|important] [[Control System Engineering.pdf#page=407&selection=123,0,151,1&color=yellow|Control System Engineering, p.316]]
> > The root locus begins at the finite and infinite poles of G(s)H(s) and ends at the finite and infinite zeros of G(s)H(s).

> [!PDF|yellow] [[Control System Engineering.pdf#page=407&selection=230,16,241,4&color=yellow|Control System Engineering, p.316]]
> >  If the function approaches infinity as s approaches infinity, then the function has a pole at infinity
> 
> 

> [!PDF|note] [[Control System Engineering.pdf#page=407&selection=241,6,250,5&color=note|Control System Engineering, p.316]]
> > If the function approaches zero as s approaches infinity, then the function has a zero at infinity.

> [!PDF|yellow] [[Control System Engineering.pdf#page=408&selection=1,1,43,5&color=yellow|Control System Engineering, p.317]]
> > G s s has a pole at infinity, since G(s) approaches infinity as s approaches infinity. On the other hand, G s 1 s has a zero at infinity, since G(s) approaches zero as s approaches infinity.


- Important
> [!PDF|important] [[Control System Engineering.pdf#page=408&selection=44,0,54,20&color=important|Control System Engineering, p.317]]
> > Every function of s has an equal number of poles and zeros if we include the infinite poles and zeros as well as the finite poles and zeros


> [!PDF|yellow] [[Control System Engineering.pdf#page=408&selection=85,0,106,5&color=yellow|Control System Engineering, p.317]]
> > Each s in the denominator causes the open-loop function, KG(s)H(s), to become zero as that s approaches infinity. Hence, Eq. (8.26) has three zeros at infinity.


> [!PDF|important] [[Control System Engineering.pdf#page=408&selection=107,22,122,10&color=important|Control System Engineering, p.317]]
> > the root locus begins at the finite poles of KG(s)H(s) and ends at the infinite zeros

> [!PDF|yellow] [[Control System Engineering.pdf#page=408&selection=152,0,165,11&color=yellow|Control System Engineering, p.317]]
> > The root locus approaches straight lines as asymptotes as the locus approaches infinity. Further, the equation of the asymptotes is given by the real-axis intercept, σa and angle, θa as follows:

![[Control System Engineering.pdf#page=408&rect=105,304,455,429&color=yellow|Control System Engineering, p.317]]

> [!PDF|yellow] [[Control System Engineering.pdf#page=410&selection=44,0,52,45&color=yellow|Control System Engineering, p.319]]
> > We now discuss how to refine our root locus sketch by calculating real-axis breakaway and break-in points, jω-axis crossings, angles of departure from complex poles, and angles of arrival to complex zeros

> [!PDF|yellow] [[Control System Engineering.pdf#page=410&selection=79,3,97,0&color=yellow|Control System Engineering, p.319]]
> > The point where the locus leaves the real axis, σ1 , is called the breakaway point, and the point where the locus returns to the real axis, σ2 , is called the break-in point

![[Control System Engineering.pdf#page=411&rect=221,456,522,713&color=yellow|Control System Engineering, p.320]]

> [!PDF|yellow] [[Control System Engineering.pdf#page=411&selection=3,38,18,0&color=yellow|Control System Engineering, p.320]]
> > As the two closed-loop poles, which are at 1 and 2 when K 0, move toward each other, the gain increases from a value of zero. We conclude that the gain must be maximum along the real axis at the point where the breakaway occurs, somewhere between 1 and 

> [!PDF|note] [[Control System Engineering.pdf#page=411&selection=18,3,19,72&color=note|Control System Engineering, p.320]]
> > Naturally, the gain increases above this value as the poles move into the complex plane

![[Control System Engineering.pdf#page=411&rect=207,78,546,245&color=important|Control System Engineering, p.320]]

> [!PDF|important] [[Control System Engineering.pdf#page=411&selection=33,4,43,1&color=important|Control System Engineering, p.320]]
> > sketch in Figure 8.14 shows the variation of real-axis gain. The breakaway point is found at the maximum gain between 1 and 2, and the break-in point is found at the minimum gain between 3 and 5

> [!PDF|yellow] [[Control System Engineering.pdf#page=412&selection=1,1,11,27&color=yellow|Control System Engineering, p.321]]
> > finding the points at which the root locus breaks away from and breaks into the real axis. The first method is to maximize and minimize the gain, K, using differential calculus

### jw crossings
> [!PDF|important] [[Control System Engineering.pdf#page=414&selection=36,47,52,9&color=important|Control System Engineering, p.323]]
> > The jω-axis crossing is a point on the root locus that separates the stable operation of the system from the unstable operation. The value of ω at the axis crossing yields the frequency of oscillation, while the gain at the jω-axis crossing yields, for this example, the maximum positive gain for system stability

> [!PDF|yellow] [[Control System Engineering.pdf#page=414&selection=56,0,68,40&color=yellow|Control System Engineering, p.323]]
> > To find the jω-axis crossing, we can use the Routh–Hurwitz criterion, covered in Chapter 6, as follows: Forcing a row of zeros in the Routh table will yield the gain; going back one row to the even polynomial equation and solving for the roots yields the frequency at the imaginary-axis crossing

### angle of departure and arrival
> [!PDF|yellow] [[Control System Engineering.pdf#page=415&selection=48,52,51,86&color=yellow|Control System Engineering, p.324]]
> > Consider Figure 8.15, which shows the open-loop poles and zeros, some of which are complex. The root locus starts at the open-loop poles and ends at the open-loop zeros. In order to sketch the root locus more accurately, we want to calculate the root locus departure angle from the complex poles

- The angle of departure for a pole can be found by considering a point that is $\varepsilon$ close to the pole in question.
- Since the sum of angles at a pole sum to an odd multiple of 180, we can solve 
![[Control System Engineering.pdf#page=416&rect=98,487,434,712&color=yellow|Control System Engineering, p.325]]

### plotting and calibrating
> [!PDF|yellow] [[Control System Engineering.pdf#page=417&selection=9,46,13,94&color=yellow|Control System Engineering, p.326]]
> > Let us assume we want to find the exact point at which the locus crosses the 0.45 damping ratio line and the gain at that point.

- We search for the correct gain $K$ in order to meet an overshoot criteria
- Remember that the point on the root locus is how the poles have moved, so if we solve for when there is a pole along the overshoot line, then we have found the gain to meet that overshoot criteria
> [!PDF|important] [[Control System Engineering.pdf#page=417&selection=20,10,27,0&color=important|Control System Engineering, p.326]]
> >  If a few test points along the ζ 0 45 line are selected, we can evaluate their angular sum and locate that point where the angles add up to an odd multiple of 180

> [!PDF|yellow] [[Control System Engineering.pdf#page=417&selection=33,1,44,53&color=yellow|Control System Engineering, p.326]]
> > electing the point at radius 2 r 2 on the ζ 0 45 line, we add the angles of the zeros and subtract the angles of the poles, obtaining

> [!PDF|yellow] [[Control System Engineering.pdf#page=418&selection=37,0,49,0&color=yellow|Control System Engineering, p.327]]
> > In summary, we search a given line for the point yielding a summation of angles (zero angles–pole angles) equal to an odd multiple of 180°. We conclude that the point is on the root locus. The gain at that point is then found by multiplying the pole lengths drawn to that point and dividing by the product of the zero lengths drawn to that point


## Summary of Rules for Plotting
![[Control System Engineering.pdf#page=419&rect=196,72,569,620&color=yellow|Control System Engineering, p.328]]
