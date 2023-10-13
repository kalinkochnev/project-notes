- Sequential containers include:
	- vector, list, dequeue, arrays, forward_list
- There are adapters for different sequential containers: 
	- queue, priority queue, stack
- **Associative containers**: Implemented sorted data structure for fast search
	- set, multiset, map, multimap
- **Unordered associative containers**: data structures for unordered data to quikcly search
	- unordered_set, unordered_multiset, unordered-Map, unordered_multimap 

# Iterators
- Abstraction for indexes into containers
- Set the start and end of the iterator and can go next or even random access
- Containers can manufacture iterators
	- ex: `vector<int>::iterator` or `vector<int>::reverse_iterator`
- `*` gets item at current index, `++` moves forward
	- can write into item at current index with `*`
- `vector.end()` points one index past the last element

