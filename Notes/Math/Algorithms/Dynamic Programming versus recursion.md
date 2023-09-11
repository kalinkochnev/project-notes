I will be referring to the LCS problem (least common subsequence) throughout.

- The only difference between recursion and dynamic programming is that recursion starts at LCS(M, N) while dynamic programming starts at LCS(0, 0).
- Recursion is reverse induction, while dynamic programming is induction

# Dynamic programs as tables
https://lcs-demo.sourceforge.net/
I am trying to understand the LCS algorithm. What I don't exactly understand is `max(T[i-1, j], T[i, j-1])` in the recurrence. I get that we are essentially propagating the best LCS for smaller strings. But what significance does The (i-1, j) and (i, j-1) strings have? In the edit distance it represented inserting a space which I understood. But here I am kind of lost.

>I think I kind of get it now So let's say I am filling out the table forwards and I know that `A[i] != B[j]`. 
>Imagine I am currently standing at the spot `T[i-1, j-1]` I can either go down with `T[i, j-1]` or right with `T[i-1, j]` 
>I want to make the decision that is best for me. Right or down 
>I know that an optimal decision now will always lead to the best solution later. It is not like I will miss out by exploring a the locally optimal path since strings/the solution builds up. 
>If I make a worse decision earlier on, it will lead me to a worse outcome in the end. A dynamic program is not a greedy algorithm because even though both are locally optimal, dynamic programs make the best decisions at every choice because solutions build upon one another.

>When I looked at it from the perspective of starting at `T[i-1, j-1]`, things made a lot more sense to me. 
>When I was filling out the table, I was looking at it from the perspective of `T[i, j]` so if I was doing `T[i-1, j]` from the perspective of `T[i, j]`, that would be the equivalent of moving backwards a character which is unintuitive 
>But from `T[i-1, j-1]`, doing `T[i, j-1]` is equivalent to taking a step in the correct direction by adding a character