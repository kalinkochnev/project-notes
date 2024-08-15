Suppose we have a probability space consisting of a sample space S, $\sigma$-field $F$, and a probability $P$ on $F$.

**Def:** Two events $E,F \in \mathscr{F}$ are independent if $P(E \cap F)=P(E)P(F)$ 
**Proposition**: if $E$ and $F$ are independent, $E^C$ and $F^C$ are independent

**Def:** Let $A_{1}\dots A_{n} \subset S$ we say that the events are jointly (mutually) independent if for all possible sub collections $i_{1}\dots i_{r} \in {1\dots n}$ where $1\leq r\leq n$ we have
$$P(\bigcap^r_{k=1} A_{i_{k}}) = \Pi_{k=1}^r P(A_{i_{k}})$$



# Examples
### Suppose we flip two coins. If A=tails on coin 1 and B=heads on coin 2.
Sample space is ${TT, TH, HT, HH}$. Since there $\frac{1}{4}$ outcomes have a tails
$$
P(A \cap B)=\frac{1}{4} = P(A)P(B)=\frac{1}{2} \frac{1}{2}
$$
=> therefore A and B are independent events

### Say we roll 2 fair dice Let $E :=\text{sum is 7}$, $F:= \text{first die rolls 3}$, $G:= \text{second die rolls 4}$ 
1) We want to see if these events are independent. List all the outcomes for each
$E={(1,6), (2, 5), (3, 4), (4, 3), (5, 2), (6,1)}$
$F=\{ (3,1), (3, 2), (3, 3), (3, 4), (3,5), (3,6) \}$
$G=\{ (1, 4), (2,4 ), (3, 4), (4,4), (5,4), (6,4) \}$

2) Number of ways to roll 2 die are $|S|=36$
$P(E)=\frac{6}{36}=P(F)=P(G)$ 

3) Find the all intersections between subcollections of elements
$$
\begin{align}
E \cap F=\{ (3,4) \} \\
E \cap G=\{ (3,4) \} \\
F \cap G = \{ (3,4) \} \\
E \cap F \cap G = \{ (3,4) \}
\end{align}
$$
$$
\begin{align}
P(E \cap F)=\frac{1}{36} = \frac{1}{6} \frac{1}{6} \\
P(E \cap G)=\frac{1}{36} = \frac{1}{6} \frac{1}{6} \\
P(F \cap G)=\frac{1}{36} = \frac{1}{6} \frac{1}{6} \\
P(E \cap F \cap G)=\frac{1}{36} \neq \frac{1}{6} \frac{1}{6} \frac{1}{6}
\end{align}
$$
=> Therefore, the three events are not jointly independent (but are pairwise independent)

### What is the probability that exactly three 5's show up when I roll 10 dice
1) Pick 3 five slots
$P(5),P(5) ,P(5) ,P(other), \dots P(other) = \frac{1}{6} \frac{1}{6} \frac{1}{6} \frac{5}{6} \frac{5}{6}\dots \frac{5}{6} = \left( \frac{1}{6} \right)^3 (\frac{5}{6})^{7}$ 

2) Multiply by number of ways to arrange 10 slots
There are ${10 \choose 3}$ ways to choose which slots/dies are three 5s

3) Total probability is $P(\text{exactly 3 fives})={10 \choose 3}\left( \frac{1}{6} \right)^{3}\left( \frac{5}{6} \right)^{7}$


# Bernoulli Trials/Binomial distribution
If an experiment has success probability $p$, then the probability of $k$ successes in $n$ trials is 
$$
P(\text{k successes in n trials}) = {n \choose k}p^{k}(1-p)^{n-k}
$$


## Examples
#### The WBB has 0.65 chance of winning. What's the probability that they win 5 out of the next 7 games
$P(\text{5 wins in 7 games})={7 \choose 5}(0.65)^5 (1-0.65)^{2}$