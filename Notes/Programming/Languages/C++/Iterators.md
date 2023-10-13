- Abstractions for indexing in containers without knowing underlying structure
- Containers manufacture iterators (give front/end, and what direction iterating `:iterator/:reverse_iterator`)
	- reverse begin/end is `rbegin()/rend()`
- `auto` can be used for local variables or return types but not for function arguments

- The "last" element is one index past the end element in the container (we do not index this)
```
L = [o o o o o o o o o] X
				     ^  ^-- the "last" element that is out of bounds
					 |----- actual last element	
```

# Operations
- Point to beginning `k=0`
- Point past the end `k=n`
- Move forward/backward `k++/k--`
- Move index to a "rank i" `k=i`
- Get value/assign at index `*`



