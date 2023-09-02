## 1) Prove that if A, B, and C are sets then
$$
A - (B \cap C) = (A - B) \cup (A-C)
$$
- use x in A and x in B and C 
$$
\begin{align}
= (a \in A) \wedge \sim (b \in B \cap c \in C) \text{ by def of set subtraction} \\
= a \in A \wedge \sim (b \in B \wedge c \in C) \text{ by def of intersection} \\
= a \in A \wedge(b \notin B \vee c \notin C) \text{ by demorgan's law}\\
=(a \in A \wedge b \notin B )\vee (a \in A \wedge c \notin C) \text{ by OR distributive law} \\
=(A-B) \cup(A-C) \text{ by def of set subtraction}
\end{align}
$$

## 2) Prove if A and B are sets, then $A \times (B \cup C)=(A \times  B) \cup (A \times C)$
Observe the following sequence of equalities

## 3) Prove that if A and B are sets, then $A \subseteq B$ iff $A-B=\emptyset$
We will proceed with a direct proof. Assume that A and B are sets and $A \subseteq B$. By definition of subset, for all $x \in A$ it is also in $B$. 

$A-B$ is defined as all the elements that are in A but are not in B. Since all $x$ are in A and B, then there are no elements where $A - B$ are true. So $A-B=\emptyset$

We will now prove the converse by contradiction. Assume that $A-B=\emptyset$ and $A \nsubseteq B$. 
A is not a subset of B, which mean there exists an $x \in A$ that is not in B. By definition of set subtraction $A-B = \emptyset$. This implies that there are no elements in A that are not also in B. This is a contradiction because we showed earlier that such an element must exist because they are not subsets of each other. Therefore, if and only if $A-B=\emptyset$, then $A \subseteq B$.


Assume that is A and B a

## Extra
- Perfect divisors, less than number than itself
- Imperfect divisor, including the number so if x=28, 28 is improper divisor
- Perfect number also improper + proper divisors = 2 (perfect number)
- $\sigma (n)$ sum of divisors of number
- No primes are perfect numbers because then $\sigma(p)=1+p=2p$ which is only true for $p=1$
- $\sigma(p^{n})=1+p+p^{2}\dots+p^{n}$
- This is a geometric series, $1+p+p^{2}+\dots+p^{n}=\frac{p^{n+1}-1}{p-1}$
- No prime power is perfect
- To have it perfect, $\sigma(p^{n})=2p^{n}$
- No perfect primes and no perfect powers

This article highlights the mystery behind perfect numbers. This is an introduction to one of many examples in number theory where a set of numbers are easy to describe but are difficult to find how to get one mathematically. As we covered in class, perfect numbers are ones that are divisible by the sum of its positive divisors. The article also discusses an alternative definition, such as when a number is divisible by its positive divisors including itself. This definition is equal to $2n$ where $n$ is the perfect number. 

The majority of the article discusses different ways to try and elucidate some hidden structure in perfect numbers. We create a function $\sigma(n)$ which is defined as the sum of $n$'s divisors, which is helpful for analysis. The article derives Euclid's conjecture, which states that $M=2^{k}(2^{k+1}-1)$ is a perfect number when $2^{k+1}-1$ is prime. This was aided by the discovery that the sum of a number's divisors is equivalent to the multiplying the number's prime factors sum of divisors. Meaning, if I have the number 28, its factors are 1,2,4,7,14,28. So $\sigma(n)=\sigma(2^{2})\sigma(7)=56$.

Overall I thought it was an interesting read and connected nicely with what we learned in class. I think the most interesting aspect of this article was how we could glue together somewhat distant facts to prove and disprove what numbers can and cannot be perfect. I appreciate the derivation of the geometric series and the overall thoroughness of the author in explaining the concept. I wasn't left any gaps in knowledge. I think the aspect that most aided in my understanding was the introduction of the $\sigma(n)$ function. 

## Suppose that n is an odd number and $M=2n$ is perfect. Show that $n$ must equal 3


