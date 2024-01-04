- Structs have everything public by default. Classes opposite. Everything is private
- Header files acts as prototypes/contract of implementation

### Visibility
- Can insert `public:` or `private:` inside of structs/classes to change visibility
```c++
struct Student {
    Student();
    Student(const Student& s2);
    Student(Student&& s2);
    ~Student();
private:
    string _name;
    double _midterm, _final;
    vector<double> _hws;
}
```


# Abstract classes
- Can have partial implementations. Cannot instantiate if not fully complete
- Do not carry state. Pure interface.
- Need to use `virtual` to indicate abstract
- `= 0;` means do not expect implementation. Known as pure methods
```c++
class AStudent {
public:
	virtual void read(std::istream& is) = 0;
	virtual void print(std::ostream& os) = 0;
}
```

- Can call methods on a type that implements an abstract class with a [[Pointers#Smart Pointers]]
```c++
#include <memory>
shared_ptr<AStudent> shared(new Student);
```

# Inheritance
- Common mistake: if method signature of methods defined in abstract is slightly wrong in inherited, the method gets overloaded (same name different signature) instead of overrided (same signature different functionality)
```c++
class Student: public AStudent {} // example inheritence of abstract class
```

- `final` keyword says that you cannot override this method ^e6ecd3