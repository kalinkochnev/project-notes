# Convergence
- Absolute convergence means however you rearrange the order of the summation, you get the same answer
- Conditional convergence means rearranging may lead to a different result

# Series
$$
\frac{1}{1-x}=1+x+x^2+x^{3}+\dots
$$
- Absolutely convergent - absolute value of series will converge to a value
# Fundamental theorem of calculus
```latex
\textbf{Part 1:}


\textbf{Part 2:}
Let $f(x)$ be a continuous function on the closed interval $[a, b]$ and $F(x)$ be an antiderivative of $f(x)$ on $[a, b]$. Then,
\[\int_{a}^{b} f(x) \, dx = F(b) - F(a).\]
```
Let $f(x)$ be a continuous function on the closed interval $[a, b]$. Define a function $F(x)$ by
$$F(x) = \int_{a}^{x} f(t) \, dt.$$

Then, $F(x)$ is continuous on $[a, b]$ and differentiable on $(a, b)$, and $F'(x) = f(x)$ for all $x \in (a, b)$.