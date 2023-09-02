**Graph**: a collection of vertices and edges where each edge connects two (not necessarily distinct) vertices
![[Pasted image 20230321114035.png]]
**Cycle**: A sequence of distinct edges that ends where it began
**Tree**: a connected graph with no cycles

## Conjecture: A tree w/ n vertices has n-1 edges

### Base case
Assume that the tree has one vertex. Since any edge creates a cycle, the tree must have 0 edges.
1 vertex has 0 edges. Base case holds

### Inductive step
Assume a tree with $j$ vertices has $j-1$ edges and $1 \leq j \leq k$ (up to some maximum number of vertices k). 

Consider a tree with $k+1$  vertices. Remove one edge.
If the graph is still connected, then it must have had a cycle. By contradiction, then it is not a tree. Therefore you must get two separate graphs, neither of which has cycles so both must be trees.

The first tree has $m$ vertices and the second $l$ vertices. The total number of vertices remains the same where $m+l=k+1$. Therefore, we know that each tree when split off must have verticles $1 \leq m,l \leq k$ which we know how to handle

By our inductive hypothesis, one tree has $m-1$ edges and the other $l-1$ edges. Overall, there are $(m-1) + (l-1)=m+l-2$ edges in total with the split trees. However, since we removed one.  So $m+l-2+1=m+l-1$

We know $m+l=k+1$, so $m+l-1=(k+1)-1=k$ edges.
Now we have shown that with a tree with $k+1$ vertices has k edges.

So by strong induction, tree w/ n vertices has n-1 edges.

### Comments
- We don't need to add more base cases b/c the inductive step applies when going from $n=1$ to $n=2$
