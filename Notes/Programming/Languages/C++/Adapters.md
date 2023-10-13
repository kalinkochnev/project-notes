- Allows for better composition of algorithms

### Example

- This code doesn't work because `mycopy()` attempts to append values at indexes >= `b.end()`. This is illegal since iterators can only point to indices that already exist
- We need a way to add a new element before iterating
```c++
vector<int> a = {1, 2, 3, 4};
vector<int> b = {1, 2, 3, 4};
mycopy(a.begin(), a.end(), b.end()); // WARNING does not work
mycopy(a.begin(), a.end(), back_inserter(b))
```
- `back_inserter()` increases the length of the collection by 1 so `b.end()` is a valid place. It returns a new type of iterator with this property


- InputIterator provides start and end for one iterator
- OutputIterator is second type of iterator you want to assign to

```c++
template <typename InputIterator, typename OutputIterator>
OutputIterator mycopy(InputIterator from, InputIterator to, OutputIterator into)
{
	while (from != to) { // while not done copying
		*into = *from; // assign value from one iterator into another
		++from;
		++into;
	}
	return into;
}
```