# Quiz for Manny: level 1

passing grade: 60% (84 points)

## Concepts (10 * 7 points each)

- Interpreted vs compiled language
  - is JavaScript interpreted or compiled?
  - explain the pros
  - explain the cons

- var vs let vs const
  - when to use var
  - when to use let
  - when to use const
  - what is hoisting in JavaScript

- === vs ==
  - when to use ===
  - when to use ==

- reference type vs primitive type
  - what's the output? 
    ```js
    let o1 = { a: 1 };
    let o2 = o1;
    o2.a = 3;
    console.log(o1 == o2); 
    console.log(o1.a); 
    ```
  - why?

- undefined vs null
  - meaning of undefined?
  - meaning of null?
  - what's the output the following
    ```js
    0 == false
    ```

- arrow function vs normal function
  - rewrite the following function to arrow function
    ```js
    let sum = function(a, b) {
      return a + b;
    };
    ```
  - name at least two differences between arrow function and normal function

- string manipulation
  - name two ways to combine str1 and str2 into the expected output (in one line)
    ```js
    let str1 = "hello"
    let str2 = "Manny!"
    // expect output: "hello Manny!"
    ```
  - what's the ouput of 
    ```js
    console.log(2 + 2 + '1' );
    ```

## Labs (20 points + 20 points + 30 points)
- Array methods: map & filter
  use only map & filter methods to transform the following input array to output array
  - input: [1,2,3,4,5,6,7,8,9,10]
  - output: [9,16,25,36,49]

- react: functional vs class-based components
  - create a new react project using npm and create-react-app package
  - create a class based component
  - create a functional based component
  - prove both components are working by displaying both components in the **App** component
  - explain when to use functional component
  - explain when to use class-based component

- react: 
  - display the following list of numbers on the screen: [1,2,3,4,5,6,7,8,9,10]
    - it should be shown line by line:  like this:
      ```js
      1
      2
      3
      ...
      ```
    - the numbers must be stored as state
  - number on odd number of line should appear red
  - number on even number of line should appear blue
  - number on the last line must appear yellow (regardless even or odd)
  - add a button to the component
  - when the button clicks
    - add a random number below the current last line
