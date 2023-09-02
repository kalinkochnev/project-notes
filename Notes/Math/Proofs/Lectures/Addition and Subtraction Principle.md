**Addition principle:** If a finite set $X$ can be decomposed as $X=X_{1} \cup X_{2}\cup\dots \cup X_{n}$ where there is no overlap between partitions, then $\mid X\mid = \mid X_{1}\mid+\dots+\mid X_{n}\mid$

**Subtraction principle:** If $X \subseteq U$, then $\mid U-X\mid = \mid U \mid-\mid X\mid$

### Example: How many even 5 digit numbers are there where the digit $6$ appears exactly once
- Break into cases where the $6$ appears in each spot independently
- $6 ----$ has (1) * 9 * 9 * 9 * 4 options (4 since last digit must be even)
- $-6---$ has 8 * (1) * 9 * 9 * 4 options (8 b/c can't start with 0)
- $--6--$ has 8* 9 * 1 * 9 * 4
- $---6-$ has 8 * 9 * 9 * 1 * 4
- $----6$ has 8 * 9 * 9 * 9 * 1

- Since these cases are all distinct/ don't overlap, we can add them up all together to get number of combinations

### Example: how many integers between 1 and 1000 are not divisible by 3
- Answer by looking at the complement and finding how many integers are divisible by 3
3, 6, 9, 12 .... 999 can be re-written as (3 * 1), (3 * 2) ... (3* 333)
- This automatically counted for us, so there are 333 that are divisible by 3
- Therefore, 1000-333=667 are not divisible by 3
- Therefore, 1000-333=667 are not divisible by 3
-