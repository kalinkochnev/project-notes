[[Classes]]
[[Inheritance]]
- Static binding call correct methods based on type (function takes pointer of that type)
```c++
C_getA(X* this) -> int
```
- Dynamically dispatched methods are a table containing pointers to functions (doesn't change after compile time)

# Deallocation
- The true type of an object is not reflected in the static type (due to inheritence)
```c++
UGrad* s2 = new Grad("Billy", 67);
```

- We want virtual destructors
- Constructors as well as destructors are called up/down the chain
	- aka classes with virtual destructors should only delete the attributes they are responsible for since the superclasses with deallocate theirs
```c++
virtual ~UGrad();
```