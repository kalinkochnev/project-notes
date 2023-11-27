Describes how to assembled classes into larger structures while keeping structures efficient and reduce coupling
# Composite patterns
- Treats a composite object the same as the atomic objects
- Makes sense if the model of your system can be represented as a tree

ex: a `Box` can hold several `Products` and/or smaller boxes
![[composite problem.png]]
# Solution
- Treat the leaf object the same as the composite object
![[composite solution.png]]


# Bridge
- Can split a large class or closely related classes into two separate hierarchies, one abstract and another the implementation

### Problem
![[bridge problem.png]]
### solution
![[bridge solution.png]]

![[bridge uml.png]]
- `Abstraction` provides high level control logic. `Implementation` declares interfaces that are common to all implementation

# Proxy
- Is a placeholder/temporary substitute for another object
- It controls access to the object and performs extra functionality before it gets to the original object


### Database queries
- You might want to cache the result to database queries and not have to re-access the same information.
![[proxy.png]]

# Decorator
- lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors.
- by composing objects together you can extend functionality