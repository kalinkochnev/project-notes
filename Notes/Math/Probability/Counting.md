[[Notes/Math/Proofs/Lectures/Counting|Counting]]
[[Counting Subsets]]
# Why you don't divide by the ordering of items when doing combinations?
![[Pasted image 20240218211904.png]]


All the multiplication principle says is that the total number of outcomes for making $i$ choices is the multiplication of the number of possible outcomes at each choice $\Pi C_{i}$ .
Lets say we want to pick an item from bag A and and another item from the same bag without replacement and there are 4 items in the bag. Then we might get $4 \cdot 3$. However the ordered pair outcome $(4, 3)$ or $(3, 4)$ are fundamentally equivalent, so we divide by $2!$ to not overcount. This is exactly identical to ${4 \choose 2}$. 

See these posts:
https://math.stackexchange.com/a/3008458/873153
**https://math.stackexchange.com/q/3008508/873153**