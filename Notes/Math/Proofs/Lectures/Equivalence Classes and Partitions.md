[[Relations#Equivalence relations]]
**Set partition:** A partition of a set A is a set of non-empty subsets of A such that the union of all the subsets = A but the intersection of any two different subsets is $\emptyset$


## **Theorem:** Suppose R is an equivalence relation on a set A. Also suppose that $a,b \in A$. Then $[a]=[b]$ iff $aRb$
($[a]$ is the set of all elements that are related to a)

(=>) Assume $[a] = [b]$. We know that since R is an equivalence relation, $aRa$, so $a \in [a]$. Since $[a]=[b]$, we get that $a \in[b]$. Thus, $aRb$.

(<=) Assume $aRb$ (show $[a] =[b]$)
Start with $c \in [a]$. Then $c R a$. We know that $aRb$, then by transitivity, $c\in[b]$ and $[a] \subseteq [b]$

Now let $d \in [b]$. So $dRb$. Thus by symmetry, $bRd$. Then since $aRb$ and $bRd$, then by transitiity $aRd$. By symmetry, $dRa$ so $d \in[a]$. Therefore $[b] \subseteq [a]$.

Thus $[a]=[b]$



## **Theorem:** Suppose R is an equivalence relation on a set A. Then the set $\{ [a]: a\in A \}$ of equivalence classes of R forms a partition of A

1. Show the $\{ [a] : a \in A\}$ has sets that are non-empty

We know that $a \in [a]$ since $aRa$. Therefore, $[a]$ is not empty for all a

2. Show the union of all subsets equals A. $\cup_{a \in A}[a]=A$. Show subsets are equal.
If $x \in \cup_{a \in a}[a]$, then $x \in [a]$ for some $a \in A$. But by definition $[a] = \{ y \in A \mid yRa \}$ which means that any element in the class must be in A. Therefore, $x \in A$.

If $b \in A$, then $b \in [b]$ which is in $b \in \cup_{a \in A}[a]$

3. Show that the intersection of any two different subsets is empty. If $[a] \neq [b]$ then $[a] \cap [b] = \emptyset$.
Prove the contrapositive. Assume that $[a] \cap [b] \neq \emptyset$. Thus if $c \in [a] \cap [b]$, then $c\in[a]$ or $c\in[b]$. So $cRa$ and $cRb$.
By symmetry $aRc$ and we know $cRb$, so by transitivity $aRb$. Thus we know $[a]=[b]$

# Discussion.
**What are the equivalence classes of $\equiv \text{ (mod 5)}$ on $\mathbb{Z}$**
