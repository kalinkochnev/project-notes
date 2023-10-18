God- The goal is to optimize a mapping that takes functions as inputs and outputs real numbers so that you find minimum/maximum of this mapping
- **Main idea:** for a given function consider how variations of that function (basically a family of functions) affect the output. By adding constraints you can find the optimal solution. 
- Examples: curve of shortest length connecting two points (brachistrochrone), maximizing area enclosed by curve
[[Lagrangian Mechanics#Principle of least action]]

# Euler-Lagrange Equation
Proof: https://en.wikipedia.org/wiki/Euler%E2%80%93Lagrange_equation#Statement
$$
\frac{\partial L}{\partial f}-\frac{d}{dt} \frac{\partial L}{\partial  \dot{f}} = 0
$$

## Proof notes
- We want to find $f$ such that has boundary conditions $f(a)=A$ and $f(b)=B$ and "extremizes" the function (colloquially action)
- **Fundamental theorem of calculus of variations:** Any slight perturbation of $f$, if it is a max/min, will result in a decrease/increase respectively (basically we move away from max/min) 
- We want to make a small perturbation to $f$ where $\varepsilon$ is small and $\eta(x)$ is a differentiable function
$$g_{\varepsilon}(x)=f(x)+\varepsilon \eta(x)$$
- If in fact we don't change $\varepsilon$ at all, so $\varepsilon=0$, then $\frac{dS}{d\varepsilon}=0$. 

# Total derivative
https://math.libretexts.org/Bookshelves/Calculus/Calculus_3e_(Apex)/12%3A_Functions_of_Several_Variables/12.04%3A_Differentiability_and_the_Total_Differential
- Represents the total change across all variables in the coordinate system with respect to another set of variables (commonly $t$)
$$f(x,y) \text{ where } x(t) \text{ and } y(t)$$
- Total change that occurs with $f$ is
$$df=\frac{\partial f}{\partial x} dx + \frac{\partial f}{\partial y} dy$$
- If $x$ also depends on $t$, then the change in $x$ is
$$dx= \frac{\partial x}{\partial t} dt$$
- So the total rate change of $f(x,y)$ is
$$
\begin{align}
df=\frac{\partial f}{\partial x} dx + \frac{\partial f}{\partial y} dy \\
df=\frac{\partial f}{\partial x} \frac{\partial x}{\partial t} dt + \frac{\partial f}{\partial y} \frac{\partial y}{\partial t} dt\\
\frac{df}{dt}=\frac{\partial f}{\partial x}\frac{\partial x}{\partial t} + \frac{\partial f}{\partial y} \frac{\partial y}{\partial t} \\
\end{align}
$$
