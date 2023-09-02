- If there is an injection from $A\to B$ but is not surjective, then $|A|<|B|$ 
 $$
|\mathbb{N}|=|\mathbb{Q}|=\mid \mathbb{Z}| <|\mathbb{R}|
$$

**Theorem:** if A is any set, then $|A|<|P(A)|$
- True for finite sets. To show for infinite sets need to show $f:A\to P(A)$ but not a bijection

**Theorem:** An infinite subset of a countably infinite set is countably infinite
**Theorem:** If $U \subseteq A$, and U is uncountable, then $A$ is uncountable

**Cantor-Bernstein-Schroder Theorem**:
If $|A|\leq|B|$ and $|B|\leq|A|$, then $|A|=|B|$
- As long as we can show there are injections $f:A\to B$ and $f:B\to A$ then we know they are equal cardinality. Don't need to come up with a bijection off the bat.

**Continuum Hypothesis**
- Is there a set $A$ with cardinality such that $|\mathbb{N}|<|A|<|\mathbb{R}|$?
- It is impossible to prove with an axiomatic system. Can assume it is true or false and it is all the same. 

# Proofs
## if A is any set, then $|A|<|P(A)|$
1) Show there exists and injection from A -> P(A) so that f: A->P(A)
where f(a)={a}
	Assume f(a)=f(b) => {a}={b} => a=b
	Therefore, so far, $|A|\leq |P(A)|$

2) Assume there is a surjection $f$ from A->P(A). Then for any $x \in A, f(x)=B$ where $B\subseteq A$
- This f(x) maps to subsets which may or may not have $x$ itself
- Take all the elements that map to sets that don't contain itself $B=\{ x \in A | x \notin f(x)\}\subseteq A$
- B must in the image

Since $f$ is surjective, there is some $a \in A$ such that $f(a)=B$

Is $a \in B$?
Case 1) Yes: means $a \in B$ => $a \notin f(a)$ => $a \notin B$
Case 2) No: means $a \notin B \implies a \notin f(a) \implies a \in B$

This is a paradox so there must have been an impossible assumption
