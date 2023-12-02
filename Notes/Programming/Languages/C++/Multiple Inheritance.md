- if multiple inheriting, need to initialize all superclasses.
	- Superclass destructors must be virtual
```c++
class A {
	int a;
	virtual ~A() {}
}
	
class B {
	int b;
	virtual ~B() {}
}

class C : public A, public B {
	// Need to init superclasses
	C(int a, int b, int c) : A(a), B(b) {
		c = c;
	}
}
```

# Memory layout
- What happens if you store a sub-class in a parent class variable with multiple inheritance? 
	- The multiple inheritance can be thought of as designating different chunks of memory layout to what you inherit from
```c++
C * p = new C(1, 2, 3);
B * bp = p; // has same address as C
A * ap = p; // different address
```
![[multipleinheritance.png]]

# Diamond problem
Consider
```c++
class A{}
class B: public A {}
class C: public A{}
class D: public B, public C {}
```

- There are two cases. If you want calling methods of `B` and `C` to affect the same instance of A, you must allow the diamond. 
- Otherwise instances of A are assumed to be independent so methods of B do not affect C and vice versa

- Can allow the diamond to occur by using virtual multiple inheritance
```c++
class A{}
class B: virtual public A {}
class C: virtual public A{}
class D: public B, public C {}
```