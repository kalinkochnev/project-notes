- There are $n (n-1)(n-2)\dots 1=n!$ different lists with n elements and no repeats

# Factorial
**Def:** If n is a non-negative integer, then n! is the number of lists n that can be made from n symbols without repetition

if n>1, n! = n(n-1)(n-2)...(1)
and 0!=1

### Why is 0!=1?
*2 explanations*
- 0!=1 b/c it is the # lists of length 0 than can be made with 0 symbols (only one is the case, $\{  \}$)
- Or look at pattern of dividing in factorial so we get 1!/1 = 1 = 0!

| factorial | value | multiplier | Amount divided by (bottom up) |
| --------- | ----- | ---------- | ----------------------------- |
| 0!        | 1     | x1         | 1!/1                            |
| 1!        | 1     | x1         | 2!/2                             |
| 2!        | 2     | x2         | 3!/3                          |
| 3!        | 6     | x3         | 4!/4                          |
| 4!        | 24    | x4         |                               |

# Permutations
A list of all the elements in A *without repetition*. It is a list b/c order matters
- Permutations = $\mid A \mid!$

### example: Let $A=\{ a,b,c, \dots, z \}$ 
How many elements of length 3 can be made from A?

#### Without repetition
- Known as k-permutations (3 in this case) of n elements (26)
$$
P(n, k)=(n)_{k} = (n)(n-1)\dots (n-(k-1))=n(n-1)\dots(n-k+1)
$$
- you subtract (k-1) times since (n) really is (n-0)
- Like picking 3 marbles from a bag without replacement



Answer: 26 * 25 * 24

#### With repetition
26 * 26 * 26 = $26^{3}$


# Discussion
Ten contestants run a race. How many possible rankings are there for first, second, and third place
(10) * (9) * (8) = 720 different possible rankings