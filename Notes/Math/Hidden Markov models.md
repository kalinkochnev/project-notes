**Purpose** 
A stochastic (random process) model that describes a sequence of possible events where the probability of the event only depends on the current state. 

![[Pasted image 20230217160048.png]]

**Transition matrix**
- This matrix represents the probability of transitioning from one state to another
$T_{ij}=\text{probability of transition from state i to j}$
$$T=\begin{bmatrix}
0.3 &0.7 \\
0.6 & 0.4
\end{bmatrix}$$
**Emission probability**
- You may not be able to observe a state specifically, but you can measure characteristics that arise from those
- Ex: you may not know what the weather is in NY, but if your friend who lives there is wearing a rain coat, it is probably raining


**Assumptions**
- Events are independent from one another
- The transition to the next state solely epends on the current state
- For a Gaussian Hidden Markov Model (which estimates time series data), the data must be normally distributed

- A N-order markov model may allow dependence on not just the current state, but also N states before