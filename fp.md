
Common Principles
	DRY (don't repeat yourself), 
	YAGNI (ya ain't gonna need it)
	高内聚低耦合（loose coupling high cohesion）
	最小意外原则（Principle of least surprise）
	单一责任（single responsibility）

Pure functions
	same input => same output
	no side effect
		state change other than its return value.
		Side effects may include, but are not limited to
			changing the file system
			inserting a record into a database
			making an http call
			mutations
			printing to the screen / logging
			obtaining user input
			querying the DOM
			accessing system state
	referential transparency
		can replace a function call with its resulting without changing the the program
	function composition
		combining two or more functions in order to produce a new function

higher order function 
	Curry
		preload a function with an argument in order to receive a new function that remembers those arguments
		partially apply a function to its arguments or create a curried function 
	composition
		Take a list of functions and return some composition

Containers, Functors, Lists, and Streams
	functor
		container which has an interface which can be used to apply a function to the values inside it. When you see the word functor, you should think “mappable”.

