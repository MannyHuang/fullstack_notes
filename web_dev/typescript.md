# TypeScript

## why typescript
- make JS stong and static type
- additional features
  - generics
  - interfaces
  - decorators
- transpiling new features for old browsers

## core types
- number
- string
- boolean
- object
- array
- tuple
- enum
- any

## other types
- union: one of the types
  - ex. number | string
- literal: specific value
- function
  - ex. () => number
- unknown: will do type check, jut not atm
- never
  - a return type of function
  - when function contains infinite loop or throws error


## Class
- private: can only access within the current class
- protect: can within class and inherited class
- getter/ setter
- static
- abstract:
  - a class that can't be instantiated but has to be extended
  - enforce child class to provide concrete implementation of certian methods
- private constructor
  - constructor cannot be newed outside of the class
  - singleton pattern = private constructor + static method to invoke the constructor

## interface
- can describe the structure of an entity
  - object
  - function
- a contract class can implement and adhere to
  - though only describe the public side
  - can work together with readonly to enforce property only intialized once through constructor
- interface can be inherited
- not compiled to JS
- interface vs custom type
  - custom type is more flexible
  - interface is more clear
  - interface can be implemented by class
- interface vs abstract classes
  - interface is all virtual
  - abstract class can be half concrete half virtue

## advanced concepts
- intersection types
  - combine other types
  - will have member properties of all types
- union types
  - one of the types
- type guards
  - typeof
  - in keyword
  - instanceof
  - discriminated union pattern
    - one common property across interfaces to allow case statements
- discriminated unions
- type casting
- indexed properties
  - used when prop name can vary, and number of props can vary
  - other named prop must have the same type
- function overloads
- optional chaining
- nullish coalescing

## Generics
- type flexibility + type safety
- pass type info to a function, to allow better type inference on the result
- can apply constraints using extends keyword
- constraint
- generic utility types
  - Partial<>
  - Readonly<>

## decorators
- a form of meta programming
  - code that improves coding experience
- just a function
- decorator executes when class is defined
- places where decorators can be added
  - class decorator
  - property decorator
  - accesor & parameter decorator


## tsc compliation setup
- tsc --init
- tsc -w