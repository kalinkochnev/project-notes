 Project Summary
> Please summarize the project you undertook this summer. Your summary should address **project objectives, methods, findings/outcomes, and the significance of those findings/outcomes**.  
> 
> Put another way, we want you to address these four questions: 1. What did you seek to do/learn through the project? 2. What did you do? 3. What did you discover/produce? 4. Why is this important?

This summer I researched how the stability analysis of fluid systems can benefit from stability analysis techniques commonly applied for control theory applications. The goal of this research project was to compare the stability results from standard methods of analysis, such as direct numeric simulation, with Lyapunov stability analysis using convex optimization. My learning goals were to become familiar with the physics of fluid dynamics, analyze the stability of time-dependent system, and how to use Matlab and HPC computing to collect results. 

The research proceeded in several stages. The first stage involved becoming familiar with the lab's prior work on stability analysis of fluid systems. I derived the governing equations for a time-dependent ocean shear flow system specified in [1, 2]. These papers were used as our basis for comparison when evaluating the accuracy our our method. The second stage of my project was spent solving the fluid system in Matlab and making adjustments to the equations and parameters to get good agreement with our point of comparison. I replicated figures and results from [1,2] using direct numerical simulation. And finally, the last stage of the project was spent programming and evaluating the proposed method on UConn's high performance computing environment. 

During my research, several hypotheses were confirmed about the Lyapunov stability analysis with convex optimization technique. The theory stated that this type of analysis provides an upper bound on the growth rate of a system.  I found that original formulation of proposition 1 in the proposal did provide an upper bound however it suffered from "overshooting" the true maximum growth rate. In other words, the upper bound was not a tight bound. An alternative linear matrix inequality makes use $\frac{dP}{dt}$ as well as $P$ for a better bound. Formulating that $\frac{dP}{dt}$ matrix is non-trivial for the same reasons as formulating the $P$ matrix in closed form. We discovered that adding a finite difference estimation of $P$ for our constraint formulation yielded significantly tightened the upper bound. 

Understanding the computational requirements of our method versus direct numerical simulation (DNS) is crucial in understanding when to apply one solution method over another. Often times in computer science there is a trade off between runtime and memory usage. In practice, an algorithm with low computational complexity can perform poorly due to large memory complexity. In practice this issue is exacerbated because large performance boosts can occur from reducing memory footprint. This is because CPU cache access are much faster than RAM accesses. This is an apparent downside of the convex optimization. For every additional time-step constraint added, a new square matrix must be stored in memory until completion of the algorithm. Meanwhile, numeric integration requires only a handful of matrices in memory at all times. With that said, the computational complexity of fluid problems can warrant this trade off. This is because with numerical simulation, there are $O(N^6)$ initial conditions to iterate over. $O(N^6)$ is a misleading classification for the complexity because $N$ is not a small integer, but an element in $\mathbb{R}^{6}$. But due to the finite precision of computers, $N$ is the largest integer representable with a $B$  bits. This limitation of computers makes it impossible to prove the upper bound of a system's stability. Fortunately, the convex optimization method does not need to consider all $\mathbb{R}^{6}$ possibilities and instead requires $O(T)$ constraints, where $T$ is the number of time steps to simulate. One additional benefit is that only a single period $T_s$ can be considered for the convex optimization, compared to numerical simulation which may need several periods in order to reach a steady state. 

The proposed method can become a critical tool to analyze fluid system stability since it converts determining stability over an infinite number of initial conditions into a tractable problem. This method can allow us to answer questions about the long term behavior of systems without having to scrutinize the step by step evolution of the dynamics. Lyapnuov stability analysis with convex optimization is a powerful tool that can unlock deeper understandings of our natural environment for use in underwater vehicle propulsion, preventing arrhythmia, and more.  

Direct Numerical Simulation
![[DNS_results.png]]

Lyapunov with Convex Optimization
![[Lyapunov_Results.png]]



**TODO**
- [ ] How does the accuracy of the upper bound change as we add more numerical discretization
- [ ] What is the algorithmic runtime of Yalmip?

# Project Adaptations
> *Projects evolve and change as you engage in them and discover new things. How did you pivot, adapt, or modify your project this summer?*

Some of our theoretical work had to change in order to get the results we were hoping for. While technically our initial results did provide upper bounds for the growth rate, it did not significantly improve upon the classical methods. The project adapted by searching for an alternative linear matrix inequality. Thankfully, there was a solution that did not require significant rework to the methods. We added the time dependent $\frac{dP}{dt}$ as a part of the linear matrix inequality.

Another challenge that occurred during the summer was in replicating the prior work necessary for our point of comparison. I spent a lot of time with my PI trying to understand the work of other researchers and replicate it. After many weeks of refining the simulation setup, we felt confident that we were computing correct results that did not match with the other research. We pivoted to a different paper that we were able to replicate results for.

# Project Experience
> *What was unexpected or surprising about your research/creative experience this summer?*

What was surprising to me was how much was able to get done in such a short period of time. Additionally, academic work is not like other forms of labor where you can power through difficulties by sheer will. Insights can often come at unexpected times. And insight is not always just a realization that improves your project. An insight is also a realization that something is wrong and needs to be fixed. The project was often 2 steps forward, one step back. But as long as I was able to pay attention to the forward progress and ignore the day to day setbacks and breakthroughs, that is what enabled me to stick through it.

# Reflection on Learning
> *What have you learned from working on/completing your SURF project? 
> What skills or attributes did you develop and/or enhance through the research process?*

My programming skills proved to be invaluable during this project. It enabled me to quickly test ideas while being able to trust my programming capabilities. I gained a lot of practice being okay with not knowing things. In the past I would often feel overwhelmed when I don't know things, but this was just a normal part of the research process. You have to start from somewhere and work your way up. I became a lot more comfortable.

# Summary Statement
> *Because of my SURF award...*

Because of my SURF award, I feel more prepared to go into an academic and research setting after graduation. Additionally, I was able to dedicate the time to contribute to original research and aim to have a publication during next semester.