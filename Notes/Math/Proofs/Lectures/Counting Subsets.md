
- With [[Factorials and Permutations]] we counted number of lists (order mattered). Now we count number of subsets (order does not matter and no repetition)

- How many ways can we pick a group of size K from N people?

## Combinations
**Definition**: If $n,k \in \mathbb{Z}^{\geq 0}$ then  ${n \choose k}$ denotes the number of $k$ element subsets from a set of $n$ elements

### example
Let n=4 and $A=\{ a,b,c,d \}$

| k   | k element subsets      | ${n \choose k}$ |
| --- | ---------------------- | --------------- |
| -1  | impossible             | 0               |
| 0   | $\emptyset$            | 1               |
| 1   | a, b, c, d             | 4               |
| 2   | ab, ac, ad, bc, bd, cd | 6               |
| 3   | abc, abd, acd, bcd     | 4               |
| 4   | $\{ a,b,c,d \}$        | 1               |
| 5   | impossible             | 0                |

## How do we find a formula for ${n \choose k}$?

$P(n,k)=\text{\# k element lists from n elements} =\frac{n!}{(n-k)!}$
- We divide by (n-k)! to simulate not including sets larger than k

Compare ${n \choose k}$ to $P(n,k)$
![[Pasted image 20230328105717.png]]
- Each columns maps to a single element in ${5 \choose 3}$ where order doesn't matter
$$
{n \choose k}=\frac{P(n,k)}{\text{\# ways to reorder k elements}}=\frac{\frac{n!}{(n-k)!}}{k!}=\frac{n!}{k!(n-k)!}
$$
- If you have k elements, the # of ways to order them is k * k-1 * ... 1 [[Counting#Counting no repeats]]

## example
How many 6 digit numbers **w/ digits 1-9** have exactly 2 even digits

1. Decide which two digits will be even
(order does matter)
- There are ${6 \choose 2}$ ways to have even numbers in different positions
2. Fix the spots 

3. How many even #'s are available for those 2 spots
- 2,4,6,8 are available for each spot so $(4)(4)$

4. Assign odd #'s to remaining spots
- $(5)(5)(5)(5)$ because options are $\{ 1,3,5,7,9 \}$

# Discussion
How many 4-digit binary strings have an odd number of 1s

1. How many ways to have a string with odd # of 1s
- one 1, three 1s

2. How many 4 digit binary strings have one 1

1000, 0100, 0010, 0001
${4 \choose 1}=\frac{P(4,1)}{1!}=\frac{4!}{1!(4-1)!}=4$

3. How many 4 digit binary strings have three 1s
-> order doesn't really matter. You just want to know how many ways you can pull out "3 digits" from the "4 digit" bag

1110, 1011, 0111, 1101
${4 \choose 3}=\frac{P(4,3)}{3!}=\frac{(4)(3)(2)}{(3)(2)}=4$

There are 8 four-digit binary strings with an odd number of ones