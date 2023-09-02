https://www.youtube.com/watch?time_continue=1059&v=nej_9pShKN0&embeds_euri=https%3A%2F%2Flms.uconn.edu%2F&source_ve_path=Mjg2NjMsMTM5MTE3LDEzOTExNywxMzkxMTcsMTM5MTE3LDEzOTExNywxMzkxMTc&feature=emb_logo
## Proving a subset
Def of subset: $\forall a \in A, \forall a \in B$


To show $A \subseteq B$ ,
### Direct proof
Assume $a \in A$ and then show $a\in B$
$\forall x$, if $x \in A \to x \in B$

### Contrapositive
- Assume $a \notin B$, then $a \notin A$


#### Example: Prove that $\{ x \in \mathbb{Z}: 2 \mid x \} \cap \{ x \in \mathbb{Z} : 9 \mid x \} \subseteq \{ x \in \mathbb{Z} : 6 \mid x \}$
Let $A=\{ x \in \mathbb{Z}: 2 \mid x \} \cap \{ x \in \mathbb{Z} : 9 \mid x \}$ and $B=\{ x \in \mathbb{Z} : 6 \mid x \}$. Assum $a \in A$. Then $a \in \{  x \in \mathbb{Z} : 2 \mid x \}$  and $a \in \{  x \in \mathbb{Z} : 9 \mid x \}$. So
$$
2 \mid a \text{ and } 9 \mid a \text{ and } a \in \mathbb{Z}
$$
So $a=2k$ and $a=9m$ where $k,m \in \mathbb{Z}$. 
So a is even and a is a multiple of nine. $m$ must be even, thus $m=2n$. So $a=9(2n)=6(3n)$ so $6 \mid a$ and $a \in \mathbb{Z}$. Thus $a \in \{  x \in \mathbb{Z} : 6 \mid x \}$. So $a \in B$, thus $A \subseteq B$.

#### Example: Prove if A and B are sets, then $P(A) \cup P(B) \subseteq P(A \cup B)$

Assume A and B are sets. Also assume that $X \in P(A) \cup P(B)$ (we can say this because really we are saying if $P(A) \cup P(B)$ then subset eq $P(A \cup B)$).

Then $x \in P(A)$ or $x \in P(B)$. Consider two cases.
Case 1: When $x \in P(A)$, then $x \subseteq A$ since $A \subseteq A \cup B$. Then $x \subseteq A \cup B$ by transitivity. So $x \in P(A \cup B)$

Case 2: When $x \in P(B)$then $x \subseteq B$ and $B \subseteq A \cup B$ so $x \subseteq A \cup B$. Thus $x \in P(A\cup B)$

## Proving is an element in a set
$A=\{ x \in S \mid P(x) \}$
- Show that $a \in A$ just by showing $P(a)$ is true and $a \in S$

## Proving equivalent
- Show $A \subseteq B$ and $B \subseteq A$
![[Pasted image 20230305195931.png]]

# Discussion
**Prove**: Suppose $A$ and $B$ are sets. If $P(A) \subseteq P(B)$ then $A \subseteq B$.
Suppose that A and B are sets and  $P(A) \subseteq P(B)$ . Let $x \in P(A)$. Since $P(A) \subseteq P(B)$, every element in P(A) must also be in the power set of B. 

By definition of the power set, $x$ is a subset of A (because the powerset is all possible subsets).  x is also a set in $P(B)$ and therefore a subset of B. Every element in x that is a subset of A is in a subset of B (since x = x). Therefore, A is a subset of B because every element in A is also in B. 

$x \subseteq A$ and $x \subseteq B$ 
$x \subseteq A \cap B$



Assume $P(A) \subseteq P(B)$. Let $a \in A$. 
Then $\{ a \} \subseteq A$ so $\{ a \} \in P(A)$
Since $P(A) \subseteq P(B)$, $\{ a \} \in P(B)$