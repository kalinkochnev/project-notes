A function is a special type of [[Relations]] -> each input gets assigned to one output

# Definition
**Def** 
Suppose that A and B are sets. A function f from A to B (denoted $f: a\to b$) is a relation $f \subseteq A \times B$ satisfying the property that for each $a \in A$ the relation f contains exactly one ordered pair of form (a,b). The statement $(a,b) \in f$ is abbreviated $f(a)=b$

- A function is a map that assigns to each element in set $A$ (**domain**) exactly one element of a set B (**co-domain**)
- $\forall a \in A,\exists!b \in B$ s.t. (a,b) $\in f$
	- $\exists!$ means exists and unique

**Example** $f(x,y)=x^{2}+y^{2}$
$f: \mathbb{R}^{2} \to \mathbb{R}$
In set notation, $\{ ((x,y), z) \in \mathbb{R}^{2}\times \mathbb{R} \mid z=x^{2}+y^{2} \}$

**Example** $f(x)=\pm \sqrt{ x^{2}+1 }$
This is not a function because it has 2 answers!

# Equality
Two function are equal if $f=g$ (as sets)

$f=\{ (a,b) \in A \times B \mid b = f(a) \}$
For all $a \in A$, there exists b s.t. $f(a)=b$, $(a,b) \in f$

$g=\{ (c,d)\in C \times D \mid d=f(c) \}$
Let $(a,b) \in f$, then $(a,b) \in g \implies g(a)=b$

$f=g$ iff $f(x)=g(x)$ for every $x \in A$

# Discussion
Is $f: Q \to \mathbb{Z}$ defined by $f(\frac{p}{8})=p+q$ a function?
![[Pasted image 20230410184924.png]]


# Injective and Surjective functions
**Range** - the set of items f maps to "the stuff that you hit"
**Co-domain** -  the entire set that could be mapped to, but may not be

![[Pasted image 20230410174436.png]]
Range $\{ 3,4 \}$, Codomain $\{ 3,4,5 \}$

# Surjective
**Surjective (onto)** - the range == codomain
If for every $b \in B$, there is an $a \in A$ with $f(a)=b$
- Suppose $b \in B$, prove there exists $a \in A$ for which $f(a)=b$

# Injective
**Injective** - every element gets mapped to a single element
If  $\forall a, a' \in A$, $a \neq a'$ => $f(a) \neq f(a')$
- Can prove with contrapositive. Suppose $f(a)=f(a')$ ... therefore $a=a'$
- Not injective, multiple elements mapped to the same element
![[Pasted image 20230410180204.png]]

## Example
Consider $f: \mathbb{R} - \{ 0 \} \to \mathbb{R}$ defined by $f(x)=\frac{1}{x}+1$
If f injective? surjective? If not, can we change the domain/codomain to make it bijective?

**Injective:** Assume that $x,y \in \mathbb{R} - \{ 0 \}$ and $f(x)=f(y)$
$$
\begin{align}
\frac{1}{x}+1 = \frac{1}{y}+1, \text{ subtracting 1 gives} \\
\frac{1}{x} = \frac{1}{y} \\
x=y
\end{align}
$$
Thus f is injective.

**Surjective:** To show it is false, we need to show there exists $b \in B$ such that for all $a \in A$, $f(a)\neq b$.
The function f is never surjective since f(x) is never equal to 1. If it was, then 
$$
\begin{align}
\frac{1}{x}+1=1 \\
\frac{1}{x}=0 \\
1=0
\end{align}
$$
Which is impossible

**Change codomain**. 
The image of f is $\mathbb{R} - \{ 1 \}$, so we need to make the codomain be $\mathbb{R}- \{ 1 \}$ to be surjective.

**Show** $f: \mathbb{R} - \{ 0 \}\to \mathbb{R}-\{ 1 \}$ is surjective with $f(x)=\frac{1}{x}+1$
Let $y \in \mathbb{R} - \{ 1 \}$. Let $x=\frac{1}{y-1}$. Note x!=0 since y!= 0. Therefore this is well defined
Thus 
$$
\begin{align}
f\left( \frac{1}{y-1} \right) = \frac{1}{\frac{1}{y-1}}+1 \\
y-1+1 \\
y
\end{align}
$$

# Pigeonhole principle
- If you have more pigeons than pigeonholes, then $f$ cannot be injective
- If you have more pigeonholes than pigeons, then $f$ cannot be surjective
![[Pasted image 20230410180350.png]]


# Discussion
Show that $g: \mathbb{Z} \times \mathbb{Z} \to \mathbb{Z} \times \mathbb{Z}$ defined by $g(m,n)=(m+n, m+2n)$ is bijective. 
Scratch: Need $g(x,y)=(a,b)$.
$$
\begin{align}
(x+y,x+2y)=(a,b) \\ \\
x+y=a \\
x+2y=b \\ \\
y=b-a \\
x=2a-b
\end{align}
$$

**Surjective:** Let $(a,b) \in \mathbb{Z} \times \mathbb{Z}$. Let $(x,y)=(2a-b, b-a)$
$$
\begin{align}
g(x,y)=(2a-b+b-a, 2a-b+2(b-a)) \\
=(a, b)
\end{align}
$$


Given any set A of 10 integers between 1 and 100, there exist two different subsets $X \subseteq A$ and $Y\subseteq A$ so $\sum X = \sum Y$

