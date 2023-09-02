**Definition:** Suppose $f: A \to B$ and $g: B\to C$ are [[Functions]] with the property that the *codomain* of f equals the *domain* of g. 
The composition of f with g is another function, denoted $g \circ f$.
If $x \in A$, then $g \circ f(x)=g(f(x))$. So $g \circ f : A\to C$


## When codomain != domain
Consider $f: A\to B$ and $g: C \to D$. When is $g \circ f(x)$ defined?
![[Pasted image 20230412130155.png]]

## example
![[Pasted image 20230412102655.png]]
- We can compoe f w/ g b/c codomain = domain
- We can't compose f w/ h b/c codomain $\nsubseteq$ domain
- We can compose g with h b/c    $\{ 1,3 \} \subseteq \{ 1,2,3 \}$

# Properties
- Not commutative
- Is associative

# Discussion
Suppose $f: A \to B$ and $g: B\to C$.

### Prove if f and g are [[Functions#Injective]], so is $f \circ g$
The composition $f \circ g(x)=f(g(x))$
If f is a function, every input has exactly one output. 
Proof by contrapositive. Suppose $f \circ g(x)=f \circ g(x')$ then
$$
\begin{align}
f \circ g(x) = f \circ g(x') \\
f(g(x)) = f(g(x')) \text{ b/c f is injective, the only way this is true is if} \\
g(x)=g(x') \text{ g is injective so it must be the case that}\\
x=x'
\end{align}
$$

# Prove if f and g are [[Functions#Surjective]], so is $f \circ g$
$g: A\to B$ and $f: B\to C$
$f \circ g : A \to C$
Want to show that $\forall c \in C, \exists a \in A$ such that $f \circ g(a)=c$ where $c \in C$
$$
\begin{align}
f \circ g(a) = c\\
f(g(a)) = c
\end{align}
$$
Since f is surjective, $\exists  b' \in B$ such that $f(b')=c$
Since g is surjective, $\exists a' \in A$ such that $g(a')=b'$

Then
$$
\begin{align}
f \circ g(a')=f(g(a')) \\
=f(b') \\
= c
\end{align}
$$
