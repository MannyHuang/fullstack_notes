# NestJs

## entities
- controller
- module
- main


## controller
- handle http requests and delegate complex tasks to providers
- registered in module controllers
- DTO: data transfer object
  - define data received at server side
- features
  - auto serialize returned JSON object
  - auto resolve async return value

## provider
- a class with @Injectable decorator
- registered in module provider
- has module scope
- examples
  - services
  - repositories
  - factories
  - helpers
- inject dependency
  - to make wiring up entity relationships can be handled by framework runtime
  - constructor-based injection
  - property-based injection

## services
- responsible for data storage, retrieval

## module
- class annotated with @module decorator
- singleton by default
- types of modules
  - application module
  - feature modules
  - shared module
  - dynamic module
- configurable properties
  - providers
    - providers to be instantiated by nest, and shared across the module
  - controllers
  - imports
    - modules that exports providers required in this module
  - exports
    - providers should be available to other modules that import this module

## middlewares
- functions called before route handlers
- a function implementing NestMiddleware interface
- have access to request and response objects
- features of middlewares
  - execute any code
  - change req, res
  - end req, res cycle
  - call next() to pass control if not ending req, res cycle
- functional middleware: middleware that is a function and requires no dependency

## pipes
- use cases
  - transformation
  - validation

## guards

## interceptors

## custom decorators


## CLI
- project init
  - nest new project_name
- file generators
  - nest g controller courses
  - nest g service courses
