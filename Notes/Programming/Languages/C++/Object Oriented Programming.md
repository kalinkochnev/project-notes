- Encapsulation (bundle things together into one package)
	- `struct`, `class` bundle together attributes of different types
- Breaking encapsulation (digging into guts and modifications) can result in unpredictable results correctness
ex: 
```c++
Rectangle * p = new Rectangle(10, 20, 100, 100);
Point p1(42, 42);
*p->getCorner() = p1; //getCorner returns shared reference to Point. This results in you being able to change the address pointed to
```

# Inheritance
- Not code mainly meant for code reuse (side effect), used to refine definitions 
	- subsets and subtypes
	- Hierarchy of classes with fewer entities meeting those requirements
- Used to define requirements
	- Demands on attributes and behaviors

### Subsumption
Let $A, B$ be types. If A is a subtype of B $A \subseteq B$, whenever a B is expected, an A can be provided
- In C++, in order to use subsumption, you must expose the inherritance as public
```c++
class Mammal {}
// if public is not included here, then code is inherited
// like copy paste, but it cannot be used as a subtype of Mammal
// public allows using a Human object as a Mammal class
class Human : public Mammal {} 
```

- In C++, the "wrong" method may be called. If I treat a human as a mammal, it will invoke the methods on the Mammal class instead of the Human class
	- This is counter-intutive compared to other languages. You would expect the the human acting as a mammal to still call Mammal methods
	- This is polymorphism!
	- Must specify if you want to use polymorphism C++  (aka dynamic binding)

### Inheritance visibility
Public inheritance (not default)
- anything inherited keeps its status
- anything overridden uses privacy setting in override

Protected inheritance: 
- Protected in general means that subclasses can use the method but outside ones cannot
- In the context of inheritance
	- Anything that was public becomes protected.
	- Anything protected becomes private
- If `class A : protected B`, means that subclasses of A are aware they inherit from B but nobody else knows

Private inheritance:
- Everything becomes private. `class A : private B` means only A knows about the inheritance

# Dynamic binding
- Using `virtual` in front of a method allows responding to messages based on dynamic type rather than compile time type (runtime polymorphism)
- The virtual key word does not need to be specified in child class implementation