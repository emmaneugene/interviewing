 List of design patterns defined within "Design Patterns - Elements of Reuabel Object-Oriented Software". Patterns prefixed with ! are more commonly encountered
## Creational
### !Builder
Separate the construction of a complex object from its representation so that the same construction process can create different representations
### !Factory 
- Abstract factory: Provide an interface for creating families of related or dependent objects without specifying concrete classes
- Factory method: Define an interface for creating an object, but let subclasses decide which class to instantiate.
### Prototype
Specify kinds of objects to create using a prototypical instance, and create new objects by copying this prototype
### !Singleton
Ensure a class only has one instance, provide a global point of access
## Structural
### !Adapter 
Convert interface of one class into another interface clients expect
### Bridge 
Decouple an abstraction from its implementation so that both can vary
### Composite
Compose objects into tree structures to represent part-whole hierarchies. Clients can treat individual and composite objects uniformly
### !Decorator
Attach additional responsibilities to an object dynamically. A flexible alternative to subclassing in order to extend functionality
### !Facade
Provide a unified interface to a set of interfaces in a subsystem.
### Flyweight
Use sharing to support large numbers of fine-grained objects efficiently
### Proxy
Provide a surrogate or placeholder for another object for access control
## Behavioral
### Chain of responsibility 
Avoid coupling the request sender to receiver by giving >1 object a change to handle the request. Chain and pass request along until it is handled
### Command
Encapsulate request as an object, allowing parameterization and undoable operations
### !Iterator
Provide a way to access elements of an aggregate object sequentially without exposing underlying representation
### Mediator
Define an object that encapsulates how a set of objects interact.
### Memento
Without violating encapsulation, capture and externalize an object's internal state so that it can be restored later
### !Observer
Define a one-many dependency between objects, so when one object changes state, all its dependents are notified
### State
Allow an object to alter its behaviour when its internal state changes. The object will appear to change its class
### Strategy
Define a family of algos, encapsulate each one, and make them interchangeable. Strategy allows the algo to vary independently from clients that use it
### Template method
Define skeleton of an algo in an operation and defer some steps to subclasses
### Visitor
Represent an operation to be performed on the elements of an object structure. Lets you define a new operation without changing the classes of the elements on which it operates

