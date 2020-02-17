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
- type guards
- discriminated unions
- type casting


## tsc compliation setup
- tsc --init
- tsc -w