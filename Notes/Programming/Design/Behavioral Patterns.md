- Concerned with algorithms and the assignment of responsibilities between objects

# Command
- Turns a request into a stand-alone object that contains all information about the request
- Can delay, queue, or support undo operations
- Promotes **separation of concerns**: each program is broken up into distinct sections that addresses a separate concern
	- prevents coupling between GUI and business logic
```c++
class Command {
public:
	virtual ~Command();
	virtual void Execute();
	virtual void Unexecute(); //undo/redo
protected:
	Command();
}
```

![[Command.png]]

# Observer
- Defines a subscription mechanism to notify multiple objects about events happening to the object they are observing
- Can add/remove observers dynamically
- Interactions between subjects/observers can be complex. Notification is not deterministic

1) Observer registers with subject/publisher (an object with interesting state)
2) Subject notifies observer about any change
3) Observer queries subject for update

![[Publisher.png]]

# Strategy
- Define a family of algorithms, put each of them into a separate class, and make their objects interchangeable

1) Context maintains ref to concrete strategy
2-3) strategy interface implemented by all concrete algorithm
4) Context calls algorithm but doesn't know how it works
![[Strategy.png]]

# Chain of Responsibility
- Can pass requests along a chain of handlers that each gets a chance to process the request or pass it on to the next handler
- Avoids coupling of sender and receiver, can easily add/remove them

- 
![[Handler.png]]

# State
- Allows an object to alter behavior when its internal state changes. Appears as if object changed its class.
- Create a new class for every possible state of an object and put all state specific behaviors into those classes
- Related to finite state machines. 

![[State.png]]