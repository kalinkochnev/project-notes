- Encapsulation hides implementation information/details
- Objects bind data and procedures that operate on data
goal: decompose problem into manageable and interacting objects

- Interface defines signature of operation/method (name, params, returns)
- Object interface = set of all signatures of operations

# Inheritance
- can build software incrementally
- Subclass defines subtype (subtype is suitable for parent type)

**Polymorphism:** `type A` can refer to object of `type B` if $A \subset B$



# OO Principles
**1) Program to an interface, not an implementation**
	- c++ does not have formal interface, use pure virtual functions
**2) Favor composition over inheritance**
	- composition is more flexible. Can change at objects at run time instead of compile time.
	- Inheritance says `Window` is a type of `Rectangle`. This relationship is too strict b/c `Window` doesn't need to be a rectangle.
	- **Delegation:** receiving object processes request by referring it to a object (highly decomposed design may be more complex)
*composition ex:*
![[Pasted image 20231029194832.png]]

**3) When designing, anticipate change**


# OO vs Procedural
- OO is flexible and easier to maintain, but is more complex and less efficient
- Procedural is better if software needs less change