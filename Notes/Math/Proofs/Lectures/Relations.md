- A relation on a set A is a subset $R \subseteq A \times A$ (all the ordered pairs that satisfy the condition R)
- Abbreviates as xRy versus $(x,y)\in\mathbb{R}$

## Relations as graphs
- Draw directed edges between ordered pairs

### ex: Consider $B=\{ 0,1,2,3,4,5 \}$ w/ $R=\{ (1,3), (2,3), (3,5), (3,1), (0,2), (0,0) \}$
![[Pasted image 20230404095947.png]]
# Properties of relations
1. Reflexivity - $\forall x \in A, xRx$
	- Ex: = is reflexive, <= reflexive, != is not reflexive
2. Symmetric - $\forall x,y \in A, xRy \implies yRx$
	1. Can switch around and get the same
	2. Ex: If x=y then y=x (true), if x<=y then y<=x (not true)
3. Transitive - if whenever xRy and yRz, then also xRz
	1. ex: if x=y & y=z => x=z (true), 
	2. ex: if x!=y and y!=z, then x!=z (false)


## Example $A=\{ a,b,c,d \}$ and $R=\{ (b,b), (b,c), (c,b), (c,c), (d,d), (b,d), (d,b), (c,d), (d,c) \}$
$\forall x \in A, xRx, i.e. (x,x)\in R$
- R is not reflexive because every element in the set must be paired w/ itself. Does not have (a,a)

If xRy then yRx.
- R is symmetric

If xRy and yRz, then xRz (hard to check)
- See that for every element there is a path that can be follow that leads to another element
- Also elements must loop to themselves (b,d) -> (d,b) => (b,b)
ex: (b,d) -> (d,c) => (b,c)

**Draw a graph to visualize**
- If all elements loop back to themselves, then they are reflexive
- To be symmetric there has to be a direct cycle between 2 elements
- Since 
![[Pasted image 20230404101520.png]]

# Equivalence relations
- Relations that are reflexive, symmetric, and transitive

**Equivalence class** - all elements in the set that are related to another element

*Formal def*: Suppose R is an equivalence relation on A. Given $a \in A$, the equivalence class containing $a$ is $\{ x \in A \mid xRa \}$. It is denoted $[a]$

### example:
- Purple = reflexive (points to itself)
- Green = symmetric (every connection has a forward/backward)
- Pink = transitive (items within an equivalence class must be fully connected)

- Each corner has a diff number of "island"/equivalence classes
	- ex: B
![[Pasted image 20230404102038.png]]


# Discussion
**Let $A=\{ 1,2,3,4,5,6 \}$. Write the relation R | where one number divides another**
$x|y = \{ (1,1), (1, 2), (1,3), (1,4), (1,5), (1,6), (2,2), (2,4), (2, 6), (3,3), (3,6), (4,4), (5,5), (6,6) \}$

**Let A=$\mathbb{Z}$, what does the relation $(a,b)\in R$ is $a \equiv b \text{ (mod 3)}$ look like?**
$\{ 0,3,6,7 \}$ are all related to 0R0
$\{ 1,4,7,10, 13\dots \}$ are all related to 1R1
$\{ 2,5, 8,11,14\dots \}$ all related to 2R2

**Determine if the relations below are reflexive, symmetric, and transitive**
|     | <   | $\mid$ | $\nmid$ |
| --- | --- | ------ | ------- |
| R   | F   | T      | F       |
| S   | F   | F      | F       |
| T   | T   | T      | F        |

**Let $n\in\mathbb{N}$. Show the relation R on $\mathbb{Z}$ given by $(a,b) \in R$ if $a \equiv b \text{ (mod n)}$ is reflexive, symmetric, and transitive**

**Proof:** Relation R is reflexive. Show that $\forall x \in A, xRx$ is true
Let $(x,x) \in \mathbb{Z} \times \mathbb{Z}$ and $R=\{ (a,b)\in \mathbb{Z} \times \mathbb{Z} : a \equiv b \text{ (mod n)} \}$
$$
\begin{align} \\
x-x=0 = 0n \\
\text{ so } n\mid(x-x) \implies x \equiv x \text{ (mod n)}
\end{align}
$$
Which is true for any n. Therefore R is reflexive
**Proof:** R is symmetric. Show that $\forall x,y \in \mathbb{Z} , xRy \implies yRx$
Assume that xRy is true.
$$
\begin{align}
x\equiv y \text{ (mod n)} \\
x-y=mn, m\in\mathbb{Z} \\
y-x=(-m)n \\
y \equiv x \text{ (mod n)}
\end{align}
$$
Therefore, R is symmetric

**Proof:** R is transitive. Show if $(xRy \wedge yRz)\implies xRz$
Let $x,y,z \in \mathbb{Z}$ and assume xRy and yRz
$$
\begin{align}
x-y=mn, m \in\mathbb{Z} \\
y-z = kn, k \in\mathbb{Z} \\
y=kn+z \\  \\
x-(kn+z)=mn \\
x-z=(k+m)n \\
x \equiv z \text{ (mod n)}
\end{align}
$$


**Find the equivalence classes for $a \equiv b \text{ (mod 3)}$**
https://www.youtube.com/watch?v=BU4eHTTgoCw
$[x]=\{ a \in \mathbb{R} : a \equiv x \text{ (mod 3)}\}$
$[0]=\{ a \in \mathbb{R} : a \equiv 0 \text{ (mod 3)} \}$ which means all items that have a remainder of 0 when divided by 3, so $\{ 0, 3, 6, 9\dots \}$
$[1] = \{ a \in \mathbb{R} : a \equiv 1 \text{ (mod 3)} \}=\{ 1,4,7,10,\dots \}=\{ 3n+1 \mid n \in \mathbb{Z} \}$
$[2]=\{ a \in\mathbb{R}: a \equiv 2 \text{ (mod 3)} \}=\{ 2, 5, 8, 11,\dots  \}=\{ 3n+2 \mid n \in\mathbb{Z} \}$


# Relations between sets
- Relations can be defined between sets
**Relation between sets** from set A to set B is a subset $R \subseteq A \times B$.