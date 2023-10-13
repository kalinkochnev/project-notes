- C++ Equivalent to Generics 
```c++
template<class T>
stack {
	void push(T e)
	T top()
	void pop()
	bool empty()
}
```

- C++ duck types templates. So if methods use the type `T`, when the substitution phase occurs in compilation, if a type does not implement a method/attribute, the c++ compiler blows up
- Can explicitly indicate type
```c++
double w = max<double>(1.0, 5.2);
```

