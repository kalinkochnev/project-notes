- Creational design patterns give flexibility when it comes to changing an implementation
1) Inheritance
2) Object composition
- Can swap out implementations are run-time and/or compile time
- Creational design tries to anticipate future changes

# Maze Example
![[maze example.png]]
- MapSite is generic maze entity (implemented as abstract class)
- Room, wall, door are all subclasses of MapSite
- This code is not flexible b/c you may have many different types of rooms, walls, doors, etc and at the moment you have to initialize everything by hand
	- should use a factory to initialize different types of maxes so that you can subclass maze and easily get new funcdtionality

# Singleton
- You want only a single instance of one class and provide global access
- Constructor is obscured and can only get instance through a method

```c++
class Singleton {
public:
	static Singleton * Instance();
protected:
	Singleton();
private:
	static Singleton * _instance;
}

Singleton * Singleton::Instace() {
	if (_instance == NULL) {
		_instance = new Singleton;
	}
	return _instance;
}
```

# Framework
- Provides existing utilities for common use cases but is still flexible enough to extend new functionality
- Allows user provided classes to be used

# Concrete Factories
- Instead of initializing objects by hand in the code, use factories to provide a centralized place to initialize common types of classes so you don't need to refactor initialization everywhere
- Uses subclasses

### Multiple document editor
![[document editor ex.png]]
- Programmer sub-classes Document and Application. Adds extra functionality
- The base classes are generic and can add the sub classed functionality easily


# Abstract Factories
- Create a family of related objects but to avoid committing to concrete classes
	- ex designing an application for different operating systems
- The factory defines the interface to be implemented by subclasses which allows swapping out the factory implementation
- Is an example of composition

![[abstract factory ex.png]]
- You override WidgetFactory for different operating systems (Motif or PM) which implement common functionality
- The implementation for widgets can be swapped used by the Client 

# Builder
- Lets you produce different types and representations of an object using the same construction code
- You might want to have lots of customization for an obj but don't want a 1000 subclasses or parameters
- Is an example of composition
### Bad
![[bad builder ex 1.png]]
![[bad builder ex 2.png]]
### Good
- Create classes designated to creating different parts of a house to enable customization
- The builder generically calls what part of the house to build, and the other class implementation takes care of customization
![[builder ex.png]]