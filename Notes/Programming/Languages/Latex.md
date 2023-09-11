Symbol name | Latex | Symbol -|- | -
Does not divide | \nmid | $\nmid$
Infinity | \infty | $\infty$
Not in | \notin | $\notin$
Piecewise | \begin{cases}\end{cases} (separated by \\\\) | $f(x)=\begin{cases}0 & x\leq 0 \\1 & x>0\end{cases}$
Bold | \textbf{} | $\mathbf{hi}$

- Regex to select all "$ $" in a document:
```
(?<!\$)\$(?!\$)
```
![[Pasted image 20230407174633.png]]

# Align with katex and Hugo
https://stackoverflow.com/questions/45971580/how-can-i-create-a-line-break-in-katex/72456257#72456257
- Use `\\\` 3 backslashes for newline
- Use `&` to align at that character
- use `\begin{aligned}` instead of `\begin{align}`

Example:
```latex
$$
\begin{aligned}
F_{j+1}&=\sum_{k=0}^{m+1}{(2m+1)-k \choose k} = \sum_{k=0}^{m+1}{2m-k \choose k}+\sum_{k=0}^{m+1}{2m-k \choose k-1} \\\
&=F_{j}+\sum_{k=0}^{m+1}{2m-k \choose k-1}  \\\
&=F_{j}+\cancel{2m-0 \choose 0-1}+\sum_{k=1}^{m+1}{2m-k \choose k-1}
\end{aligned}
$$
```

# Supported katex functions
https://katex.org/docs/supported.html
