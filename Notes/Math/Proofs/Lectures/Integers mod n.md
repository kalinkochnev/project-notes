[[Equivalence Classes and Partitions]]
- The relation $\equiv \text{ (mod n)}$ satisfy reflexivity, symmetric, and transitive, so it is an equivalence relation
- So we can consider operations $\{ [0], [1],\dots,[n-1] \}$

# Defining operations
- You can define operations on equivalence classes.
- Since they are all encompassing, the result of the operation is in the equivalence class
- 

## ex: $\equiv \text{ (mod 5)}$
![[Pasted image 20230406150036.png]]
- You can take any elements in the equivalence class, apply the operation, and it should end up in the same equivalence class
$$
[0]+[4]=\begin{align}
5+4=9 \\
20 + -16 = 4
\end{align} = [4]
$$
$$
[2]+[3]=\begin{align}
2+3 = 5 \\
7+8=15
\end{align}
= [0]
$$

## Addition and multiplication
- Addition and multiplication is well-defined on equivalence classes

## Prove
Show that for any elements $a'$ or $b'$ such that $a \equiv a' \text{ (mod n)}$ and $b\equiv b'\text{ (mod n)}$, then $[a+b]=[a'+b']$ and $[ab]=[a'b']$

Assume $a \equiv a' \text{ (mod n)}$ and $b\equiv b'\text{ (mod n)}$. So $n \mid a-a'$ and $n \mid b-b'$. So $(a-a')=nx$ and $(b-b')=ny$ $x,y \in \mathbb{Z}$. Then
$$
\begin{align}
(a-a')+(b-b')=nx+ny \\
a+b - (a' + b') = n(x+y) \\
\end{align}
$$
So $n\mid (a+b) - (a'+b')$ so $a+b \equiv a'+b'$ 


![[Pasted image 20230406150248.png]]

### proving the multiplication
Assume $a \equiv a' \text{ (mod n)}$ and $b \equiv b' \text{ (mod n)}$. Then $n \mid (a- a')$ and $n \mid(b-b')$
$a-a'=nx$  and $b-b'=ny$   $x,y \in \mathbb{Z}$

We want to show that $ab \equiv a'b' \text{ (mod n)}$,    $n \mid (ab-a'b')$, so $ab-a'b'=nz; z \in\mathbb{Z}$

Try multiplying
$$\begin{align}
(a-a')(b-b')=n^{2}xy \\
ab-ab'-a'b+a'b'=n^{2}xy
\end{align}$$
Doesn't work be ause you have middle terms that don't work. Also no minus sign on a'b'

Try $a=nx+a'$  and $b=ny+b'$ and multiply them together.
$$
\begin{align}
ab = (nx+a')(ny+b') \\
=n^{2}xy+nxb'+a'ny+a'b' \\
ab-a'b'=n^{2}xy+nxb'+a'ny \\
ab-a'b'=n(nxy+xb+a'y)
\end{align}
$$
$ab \equiv a'b' \text{ (mod n)}$

# Discussion
Find addition and multiplication tables $\text{ (mod  4)}$

If $[a][b]=[0], \text{ does } [a]=0 \text{ or } [b]=0$?
If $[2][2]=[0]$ **I'm confused on the whole prime number thing[**

No not necessarily. $[2]+[3]=[0]$ but $[2]$ can be anything with remainder 2 while $[3]$ is anything with remainder 3