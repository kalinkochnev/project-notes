- Combines state (protected by visibility) and behavior (contract through methods)
- Method overloading is when multiple methods with same name but different parameters
- Methods overriding is when you supercede an implementation with a different one (let's say a subclass overrides the parent implementation )
- Types: Default, Custom, Move, Copy

### Default/Custom
- In general you are not required to initialize attributes that are objects by hand because the default constructors are automatically called for them on class creation
	- this means you might have double initialization when doing custom initializer 
	- in the method signature you can use with colon syntax
```c++
struct Student {
    string _name;
    double _midterm, _final;
    vector<double> _hws;
    Student() { _midterm = _final = 0; }

	// This results in a string being double initialized and then 
	// reassigned. This is wasteful.
	Student(const string& name) { _name = s; _midterm=_final = 0;};

	// Alternative syntax allows you to provide your own initializer for
	// _name. Fields with colon syntax should be ordered in same order
	// they appear in def
    Student(const string& s): _name(s) { _midterm =_final=0; }
}
```

- Attributes in a class that are not initialized have the default constructor called on them automatically
- Default is called when initialized with no arguments.

### Copy constructor
- Meant to copy `x` into `y`
- Has format `T(const T&)`
```c++
Student x;
x = //...;
Student y(x); // copy x into y
```

- Compiler will automatically do a shallow copy if a copy constructor is not provided (pointer addresses are copied, objects not recursively copied) 
```c++
struct Student {
    // ... same attributes as before
	// ... all previous definitions from before
	Student(const Student &s2) {
		_name = s2._name; _midterm=s2._midterm; _final=s2._final;
		for (double d : s2._homeworks) _homeworks.push_back(d);
	}
	// Alternatively can use :field(value), field(value) initialization
	// Which calls copy constructors on those fields
	Student(const Student &s2): 
		_name(s2._name), 
		_midterm(s2._midterm),
		_final(s2._final),
		_homeworks(s2._homeworks) // 
	{}
}
```

### Move constructor
- An object created on the stack in the scope of a function only exists within that function. But what if we want to return it?
ex:
```c++
struct Complex {
	Complex scale(double f) {
		Complex c;
		c._real = _real * f;
		c._imag = _imag * f;
		return c;	
	}
}
Complex a = {1, 1};
Complex b = a.scale(2); // note (1)
```

- the object would be deallocated from stack once the function returns and the object address would be dead
- **note (1)** C++ used to create a temporary object to take the thing being returned and then eventually copying it back to something being assigned
- We can use *moves* to transfer the memory addresses directly in one go without temps

```c++
struct Student {
    // ... same attributes as before
	// ... all previous definitions from before
	Student(Student&& s2) : // a reference to a reference of a student
		_name(std::move(s2._name)),
		_midterm(s2._midterm), _final(s2._final),
		_homeworks(std::move(s2._homeworks))
	{}
}
```
- `std::move` "rips out" the scavengable parts of an object to be put into a new one
- If you implement the move constructor and want to have copy capability, you must implement both constructors manually

### Transfer operators
- Can redefine what happens when we assign objects
- `x=y=z=q;` actually passes a reference to q to z, which returns a reference to z to y, etc
- We don't modify the source `const Student&`
```c++
// Copies
Student& operator=(const Student &s) {
	// checks if assignment to self occurs to protect against x=x;
	// The references in x get deallocated and if you try to use x
	// you will have memory corruption
	if (this == &s) return *this; 
	_name = s._name;
	_midterm = s._midterm;
	_homeworks = s._homeworks;
	return *this;
}
```

- Custom move assignment disables default copy!!!!!
```c++
// Move
Student& operator=(const Student &&s) {
	_name = std::move(s._name);
	_midterm = s._midterm;
	_homeworks = std::move(s._homeworks);
	return *this;
}
```

### Destructors
- Need to release resources being held by instance
- Destructors are automatically invoked on attributes that are objects recursively (if it is implemented)
```
~Student() {

}
```
- Sometimes you do not know what you are deleting due to polymorphism

