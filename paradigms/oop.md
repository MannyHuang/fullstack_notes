# OOP: object oriented programming

## SOLID principles
- Single responsibility principle
	- A class should only have a single responsibility
	only changes to one part of the software's specification should be able to affect the specification - of the class.
- Open–closed principle
	- Software entities should be open for extension, but closed for modification
- Liskov substitution principle
	Objects in a program should be replaceable with instances of their subtypes without altering the - correctness of that program
- Interface segregation principle
	- Many client-specific interfaces are better than one general-purpose interface
- Dependency inversion principle
	- One should depend upon abstractions, not concretions

## features
- Encapsulation 
	- storing data and methods together
	- data not accessible directly from outside, only internal methods
- Inheritance
	- objects inherit properties and methods of other classes
	- adding new features without modifying existing class
- Polymorphism
	- behaviour depends on data type


## entities
	- class
		-	prototypes of things with similar data structure and behaviors
	- object
		- instantiated from class
		- basic unit of interaction at runtime 

## pros
- modular structure
- hide details
- clear interface
- extendable framework


## Choice of Construct
- base class 
	- when doesn’t pass the IS-A test for any other type.
- subclass
	- when need to need to override or add new behaviours to base class
- abstract class 
	- to define a template for subclasses
	- guarantee that nobody can make objects of that type.
	- have some implementation code that all subclasses could use
- interface
	- define a role that other classes can play, regardless of where those classes are in the inheritance tee

## General Responsibility Assignment Software Patterns
