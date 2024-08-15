**Def:** If $P(E)>0$, then the probability of event $F$ given event $E$ is 
$$
P(F|E) = \frac{P(F \cap E)}{P(E)}
$$
Alternatively
$$
P(F \cap E) = P(E) P(F | E)
$$
- What is the probability that F and E both happen at the same time?
- The probability of one event happening $P(E)$ and the other also happening given the other one happens

**Intersection is symmetric so swapping events is also possible**
$$
P(F \cap E) = P(F)P(E | F)
$$


# Bayes Rule
If $P(E)>0$ then
$$
P(F | E) = \frac{P(E|F) P(F)}{P(E|F)P(F)+P(E|F^C)P(F^C)}
$$

# "Multiplication rule"
Let $E_{1}\dots E_{n} \in F$, then 
$$
P(E_{1} \cap E_{2} \cap \dots \cap E_{n})
= P(E_{1})P(E_{2}|E_{1})P(E_{3}|E_{1} \cap E_{2})\dots P(E_{n}|E_{1} \cap E_{2} \cap \dots \cap E_{n-1})
$$
- Think of it in a similar way to $P(F \cap E) = P(E) P(F | E)$. 
- $P(E_{1})P(E_{2}|E_{1})$ gives $P(E_{1} \cap E_{2})$
- $P(E_{1})P(E_{2}|E_{1})P(E_{3}|E_{1} \cap E_{2})$ gives $P(E_{1}\cap E_{2}\cap E_{3})$


# Law of total probability
If $F_{1}, \dots, F_{n} \subseteq S$ are mutually independent (do not overlap) events with and $\cup_{i=1}^{n} F_{i} = S$ (the sample space is partition by the events), then
$$
P(E)=\sum_{i=1}^{n}P(E|F_{i})P(F_{i})
$$
![[Drawing 2024-02-05 12.24.08.excalidraw]]


## Examples
### Suppose there are 200 men, of which 100 smoke. Of 100 women, 20 smoke. What is the probability a person chosen at random smokes?
$$
P(\text{pick smoker at random})=\frac{120}{300}
$$
#### What is the probability of selecting a smoker, given we choose a woman
$$
P(\text{smoker}|\text{woman}) = \frac{P(\text{Female} \cap  \text{smoker})}{P(\text{female})}= \frac{\left( \frac{20}{300} \right)}{\left( \frac{100}{300} \right)} = \frac{20}{100} 
$$
### Suppose we roll 2 dice.
#### a) what is the probability the sum is 8
$S=\{ (3,5), (4,4), (5,3), (6,2), (2,6) \}$
$$
P(A)=\frac{5}{36}
$$
#### b) What is the probability the sum is 8 given the first die rolled is a 3?

$$
\begin{align}
P(\text{sum is 8} | \text{1st die is 3}) = \frac{P(\text{sum is 8} \cap \text{1st is 3})}{P(\text{1st is 3})} \\
=\frac{\left( \frac{1}{36} \right)}{\left(\frac{6}{36}\right)}
\end{align}
$$
- $P(\text{1st is 3})$ is the number of ways to get 3 in the first die, in general

### Suppose a box contains 3 red and 2 black marbles. If 2 marbles are chosen at random (without replacement), what is the prob. that the second marble is red given that the first is red?
$$
\begin{align}
P(\text{2nd red} |\text{1st is red}) = \frac{P(\text{2nd red} \cap \text{1st red})}{P(\text{1st is red})} \\
=\frac{\frac{{3 \choose 2}{2 \choose 0}}{{5 \choose 2}}}{\frac{{3 \choose 1}{2 \choose 0}}{{5 \choose 1}}} = \frac{\left( \frac{3}{10} \right)}{\frac{3}{5}} = \frac{1}{2}
\end{align}
$$

### A family has 2 children. Given that one of the children is a boy, what is the prob. the other is a boy?
- We don't specify which one is the boy which changes the probability (order doesn't matter)
$S=\{ bb, bg, gb, gg \}$

$$
P(\text{2 boys}|\text{1boy})= \frac{P(bb)}{P(bb, bg, gb)}=\frac{\frac{1}{4}}{\frac{3}{4}}=\frac{1}{3}
$$

**by doing conditional probability, we eliminate the girl-girl possibility**

### Suppose the test for HIV is 99% accurate in both directions (1% of false negatives + 1% of false positive), if 0.3% of people actually are HIV positive given they tested positive?
- Since the error of the test is a lot higher than the % of people who have the disease, then the probability they have the disease is lowered

$$
\begin{align}
P(\text{have HIV}|\text{test positive})&= \frac{P(\text{H+} \cap \text{Test positive})}{P(\text{test positive})} \\
&= \frac{\text{true positives}}{\text{true positives + false positives}}=\frac{(0.003)(0.99)}{(0.003)(0.99)+(0.997)(0.01)} \\
&=0.23
\end{align}
$$

### Suppose 36% of families own a dog. 30% of families own a cat, and 22% of families that own a dog also have a cat. A family is chosen at random and it is determined they have a cat. What is the probability that they also have a dog?
- $P(D)=0.36, P(C)=0.30$
- Given a family has a dog, the probability they have a cat is $P(C|D)=0.22$
- We want the probability they have a dog given they have a cat.

$$
\begin{align}
P\left( \text{D|C} \right)=\frac{P(D \cap C)}{P(C)}
\end{align}
$$
- We can actually replace $P(D\cap C)$ with the other definition of condition probability $=P(C|D)P(D)$
$$
\begin{align}
P\left( \text{D|C} \right)&=\frac{P(D \cap C)}{P(C)}  \\
&=\frac{P(D)P(C|D)}{P(C)} \\
&=\frac{(0.36)(0.22)}{0.30}=26.4
\end{align}
$$

### Suppose 30% of women make an "A" and 25% of men make an "A", and the class is 60% of women. What is the probability a person is a women given they made an A?
$$
\begin{align}
P(W|A)&=\frac{P(W\cap A)}{P(A)} \\
&= \frac{\text{woman's As}}{\text{woman's A's} + \text{mans As}} \\
&=\frac{(0.6)(0.3)}{(0.6)(0.3)+(0.4)(0.25)}
\end{align}
$$


### Monty Hall Problem
There are three doors. Behind one is a fancy new car. Behind the other two doors there are some goats. 

You choose a door. Monty Hall opens one of the other two doors revealing a goat. He gives you the opportunity to switch doors. Should you switch?

**Strategy 1**: Stay
1/3 chance of picking the door with the car on the first try

**Strategy 2**: Switch
_Case 1:_ 
	You pick the car on the first choice. 1/3 times you land in this case. Since you always switch, you lose.
*Case 2:*  
	You pick a goat on the first choice. This happens 2/3 times. 
	Since Monty always shows you the other goat, you always win. You have a 2/3 chance of winning. 
**This only works b/c monty knows where the car is and always picks the door where the car is not**

### Gambler's ruin (markov chain event)
Suppose you play a game by repeatedly tossing a fair coin. If it lands on heads, you win a dollar. If it lands on tails, you lose a dollar. Suppose you start with $50. What is the probability you hit $200 before you are ruined $0

Let $P(200|n)$ be the probability you hit 200 before $0 if you have n dollars.
You can write the current probability in terms of the future probabilities
$$
\begin{align}
P(200|n)=\frac{1}{2}P(200|n+1)+\frac{1}{2}P(200|n-1) \\
2P(200|n)=P(200|n+1)+P(200|n-1) \\
P(200|n)-P(200|n-1)=P(200|n+1)-P(200|n)
\end{align}
$$
The gain in probability from going from `n-1` to `n` is the same as the the gain in probability going from `n` to `n+1`

Since the slope of $P(200|n)$ is constant, $P(200|n)=mn+b$

We know some boundary conditions. 
$P(200|200)=1$ => m=1/200and
$P(200|0)=0$ => so b=0

So $P(200|n)=\frac{n}{200}$

#### What if I can go arbitrarily into debt
$$
0 \leq P(200|n)<1
$$
The slope must be 0 because then for sufficiently small n, we could have $P(200|n)<0$ if m!=0
Since the game never ends $P(200|n)=1$



### Bob is 80% sure he left his textbook in the union or monteith. He is 40% sure it is in the union and 40% sure it is in monteith. Given that bob checked monteith and the book wasn't there, what is the probability it is in the union?
Want to find $$P(U|M^C)=\frac{P(U \cap M^C)}{P(M^C)}$$
Since the book can't be in 2 places at once, events $U \cap M=\emptyset$.
=> Therefore $U \subseteq M^C$
=> $U \cap M^C$=$U$
=> $$
P(U|M^C)=\frac{P(U)}{P(M^C)}
$$
### Say a box has 5 red and 6 white balls. Each time a ball is drawn we replace it in the box ==along with another== ball of the same color. If 3 balls are drawn what are the odds they are all red?
Use the multiplication rule
$P(R_{1}\cap R_{2}\cap R_{3})=P(R_{1})P(R_{2}|R_{1})P(R_{3}|R_{1}\cap R_{2})$
- You have a 5/11 chance to pull a red the first time $P(R_{1})=\frac{5}{11}$
- If you already pulled a red, the new chance of getting a red is $P(R_{2}|R_{1})=\frac{6}{12}$
- Finally if you pulled two reds already, then $P(R_{3}|R_{2}\cap R_{1})=\frac{7}{13}$

$P(R_{1}\cap R_{2}\cap R_{3})=0.12$