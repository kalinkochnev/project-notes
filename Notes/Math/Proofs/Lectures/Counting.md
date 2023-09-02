**List:** an ordered collection of elements with repeats allowed $(1,2) \neq (2,1) \neq(2,1,1)$
- The number of possible options increases by a factor of N, where N is the number of new option

## Counting no repeats
![[Pasted image 20230326214245.png]]

## Multiplication principle
In making a list of length n, there are $a_{1}$ choices for the first entry, $a_{2}$ possible choices for the second entry, and so on. 
- Total # of diff lists is $a_{1} \cdot a_{2} \cdot \ldots \cdot a_{n}$


Make a list of length 4 with $\{ A,B,C,D,E,F \}$
#### Example: No repetition
How many lists are there if repetition is not allowed and the list has an E

- There are 4 different places to put an E
$E - - -$,  $-E--$, $--E-$, $---E-$
- For the last remaining 3 spots, there are 5 * 4 * 3 different options each
- Choosing the spot of E is effectively 4 more options, so total is $5 * 4 * 3 * 4 = 240$ options total

#### Example: With repetition and E is required
- Use complement of sets to help finding it
**# ALL lists w/ repetition - # lists w/o E's = # Lists w/ repetition w/ E**
$6^{4} - 5^{4} = 671$

# Discussion
A passcode has A,B,C,...Z w/ no two consecutive letters the same, how many options are available if there are 7 letters?

$26 * 25 * 25 * 25$
the first letter can be anything, the second index has only 25 choices (not same consecutive), the third index cant be the same as the second index so only 25 choices, etc

how many integers have no repeated digits from 1 to 9999? how many have at least 1 repeated digits?
![[Pasted image 20230327124851.png]]
- 





