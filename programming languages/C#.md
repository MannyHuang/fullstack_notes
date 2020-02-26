# C Sharp

## features
OOP
Component oriented programming
automatic garbage collection
exception handling
type-safe
unified types



## supported types
- value types
  - simple, enum, struct, nullable value
- reference types
  - class, interface, array, delegate

## class
- reference type
- consists of
  - data members
  - function members
    - methods, propertis
- features
  single inheritance, polymprphism

## struct types
- value type
- features
  - do not require heap allocation
  - do not support inheritance

## interface
- a contract as a set of named function members
- class or struct implement interfaces
- features
  - interface can inherit from multiple interfaces
  - class or struct can implement multiple interfaces

## delegates
- references to methods with particular params and return type
- features
  - similar to functions in functional language
  - but object-oriented and type-safe

## generics
- supported types: class, struct, interface, delegate
- allow construct to be parameterized with other types

## enum
- distinct types with named constants
- underlying type is one of the eight integral types

## statements
- types of statements
  - declaration
    - decalare local variables and constants
  - expresssion
    - method invocations
    - object allocations using new
    - assignment, increment, decrement
    - await
  - selection
    - if, switch
  - iteration
    - while, do, for, foreach
  - jump
    - break, continue, goto, throw, return, yield
  - exception handling
    - try/catch, try/finally
  - lock
    - mutual-exclusion lock (executes then release)
  - using
    - obtain a resource, execute a statement, then dispose of that resource


## class members
- methods
- constructors
- properties
- indexers
- events
- operators
- finalizers

## class accessbility
- public
- protected
- internal
- public protected
- private
- private protected

## generics
- class that takes types as parameters

## modifiers
- static
  - properties or method belongs to class
- readonly
  - assignment can only happen during declaration or in constructor
- ref
  - pass data by reference
- virtual and override
  - vritual method
    - run-time type determines actual method implementation
    - virtual method can be overriden in the derived class
  - non-virtual method
    - compile-time type determines actual method implementation
- abstract methods
  - a virtual method with no implementation
  - permitted only in abstract class
  - abstract method must be overriden in every non-abstract derived class

## parameters
- types of parameters
  - value
  - reference
  - output
  - parameter array
    - only the last param can be a param array

## static method vs instance method
- static method
  - can access static members
- instance method
  - can access static and instance members

## method overloading
- distinguish same-name class by signatures

## constructors
- instance constructor
  - implement actions required to initialize instance
- static constructor
  - implement actions required to initialize class
- instance constructor is not inherited

## properties
- natural extension of fields
- do not denote storage locations
- have accessors for read/write

## indexer
- enable objects to be indexed the same way as array

## events
- enable class or object to provide notifications

## finalizer
- automatically invoked during garbage collection
- implement finalizer when no other solution area feasible


## structs
- can contain data and function members
- value type
- do not require heap allocation, lives on the stack
- variable directly store data, not just a reference
- good use cases: complex numbers, points

# interface
- defines contract to be implemented by class and struct
- can employ multiple inheritance
- class and struct can implement multiple interfaces

# delegates
- basically function pointers, but oop and type-safe