1.1) Pointers are strongly typed and need to be coerced explicitly
1.2) ???

Exceptions.1) If no catch block catches the exception and it reaches the main function, the program crashes

Inclusion.1) The include directive inserts the specified headers to be linked with. You use `ifndef` to make sure that header files are not included more than once

Linking.1) `-c` means compile without linking?  `-g` means debugging

Iterators) Iterators are created by the container. For example, an iterator for a vector would look like `std::iterator<int> blah = myvector::iterator/myvector::reverse_iterator`

References) C++ mainly passes by value, which results in expensive copy operations. You can pass a pointer which is a value of a memory address. However you can access out of bounds. A reference is like a pointer to a specific memory address that can't be accessed outside of unless changed. Additionally a reference does not need to be de-referenced while using it. 

Templates) A template in C++ is defined as 
```c++
template <class MyType>
blah {
	MyType printValue();
}
```

Strings are allocated as a vector of chars. It is an automatically resizeable array. 