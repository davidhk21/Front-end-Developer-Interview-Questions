---
title: JavaScript Questions
layout: layouts/page.njk
permalink: /questions/javascript-questions/index.html
---

* Explain event delegation.
  - The idea of event delegation is simple. Instead of attaching the event handlers/listeners directly to child elements, you delegate listening to the parent. For example, when a button is clicked, the listener of the parent element catches the bubbling event.
  - When a click event happens (or any other event that propagates):
    - Capture Phase: The event travels down from window, document, root element and through the ancestors of the target element.
    - Target Phase: The event occurs on the target
    - Bubble Phase: Finally, the event bubbles up through the target's ancestors until the root element, document and window.
  - This mechanism is named event propagation. The event delgation is a useful pattern because you can listen for events on multiple elements using one event handler.
  - Making the event delgation work requires 3 steps:
    1. Determine the parent of elements to watch for events
    2. Attach the event listener to the parent element
    3. Use event.target to select the target elements

* Explain how `this` works in JavaScript.
  - The keyword `this` is an identifier for values (similar to a variable) that is designed to support object-oriented programming. Although `this` can be seen as complicated, it's really useful for making sure of correct object bindings to properties and methods and you'll almost exclusively see them in body of functions.
  - To determine the binding of positional parameters requires seeing call time. Call time of the function containing `this` ALWAYS dictates the binding for this. There are 5 different binding patterns possible:
    1. Method Invocation: `this` is bound to the object on the left of the call time dot. This is what `this` refers to 90% of the time.
    2. .call or .apply Invocation: `this` is set to the first argument to .call or .apply
    3. Construction Mode: `this` refers to the new object created for that invocation
    4. Free Function Invocation: `this` refers to the global object (which is window in a browser)
    5. Global Reference: `this` also refers to the global object
  * Can you give an example of one of the ways that working with `this` has changed in ES6?
    - ES6 arrow functions changed the `this` binding to a pattern called lexical scoping. The simplest way to describe lexical scoping is that the inner function (or any nested functions) have access to variables which are declared in it's outer scope.
    - For example, if an object had a method. That method would have the correct `this` binding to the original object. However, if within that method you run another function or method, `this` would be bound to the global object. In order to handle this, you'd either have to set a variable set to the correct `this` OR use .bind. However, with ES6 arrow functions, you don't have to worry about this because it changes `this` to bind using lexical scoping.

* Explain how prototypal inheritance works.
  - Prototype inheritance is a mechanism for making objects that resemble other objects.
  - When you want two objects to have all the same properties, either to save memory or to avoid code duplication, you might decide to copy all the properties over from one to the other. As an alternative, JavaScript provides the option of prototype chains. This makes one object behave as if it has all the same properties of another object, by delegating its failed property lookups to that other object at lookup time.

* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  - null: variable is defined but has no value, is a type of object
  - undefined: variable isn't defined but still declared and is a type of itself, undefined.
  - undeclared: variable is declared without 'var'
  * How would you go about checking for any of these states?
    - use `type of`

* What is a closure, and how/why would you use one?
  - Closure is a Persistent Lexical Scope Reference, meaning that when you declare a function inside another function, the inner function will have access to variables and data that share its same scope.

* What language constructions do you use for iterating over object properties and array items?
  - for loop, for...in, for each..., map, reduce

* Can you describe the main difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?
  - Array.forEach() executes a provided function once for each array element
  - Array.map() creates a new array with the results of calling a provided function on every element in the calling array

* What's a typical use case for anonymous functions?
  - When we have urgency on the return value or certain piece of code to get executed inline. Whenever it doesn't matter what name the function is it's best to just use an anonymous function.

* What's the difference between host objects and native objects?
  - Native objects are objects in an ECMAScript implementation such as Date, Math, string methods, array methods, etc.
  - Host objects are objects supplied by the host environment (browser) to complete the execution environment of ECMAScript such as window, document, location, setTimeout, getElementsByTagName, etc.

* Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
  - `function Person(){}` is a function declaration and is hoisted.
  - `var person = Person()` is a function expression but the function is executed so it returns a person which is then set to the variable.
  - `var person = new Person()` is instantiating a new object of the Person class constructor with the `new` keyword.

* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
  - `function foo() {}`:
    - hoisted
  - `var foo = function() {}`
    - not hoisted (only function expressions with var aren't hoisted, normally var variables are hoisted)

* Can you explain what `Function.call` and `Function.apply` do? What's the notable difference between the two?
  - both of them invoke the function with a defined `this` binding to them. The difference between them is how the arguments are inputted. For .call, the arguments are inputted comma delimitted but for .apply they are inputted as an array.

* Explain `Function.prototype.bind`.
  - .bind returns a function with a different `this` binding.

* What's the difference between feature detection, feature inference, and using the UA string?
  - Feature Detection: a way of determining if a feature exists in certain browsers. A good example is a modern HTML5 feature 'Location'.
  - Feature Inference: when you have determined a feature exists and assumed the next web technology feature you are implementing unto your app exists as well. It's usually bad practice to assume, so it's better to explicitlyl specify feaetures you want to detect and plan a fallback action.
  - UA string: User Agent String is a string text of data that each browsers send and can be accessed via navigator.userAgent. These "string text of data" contains information about the browser environment you are targeting. If you open your console and run 'navigator.userAgent', you'll see a string text of data containing complete information of the environment you are currently using.

* Explain "hoisting".
  - Hoisting is JavaScript's default behavior of moving declarations to the top, allowing you to use a variable before it has been declared.

* Describe event bubbling.
  - event bubbling is the last phase out of three of event propagation where the event that occurs propagates (or bubbles) up from the target element and triggers those elements until it reaches the outermost DOM element or document object.

* Describe event capturing.
  - event capturing is the first phase out of three of event propagation where the event starts from the top element to the target element, the opposite of event bubbling.

* What's the difference between an "attribute" and a "property"?
  - HTML representations of a DOM element have attributes and javascript objects have properties.
  - Sometimes changing the properties will typically update the attributes, such as changing the element.href property will update the href attribute on the element.

* What are the pros and cons of extending built-in JavaScript objects?
  - Extending a built-in JavaScript object means adding properties/functions to its prototype. Generally not a good idea to do so.
  - Pros:
    - objects can share the same method
    - failed lookups can go to its prototype
  - Cons:
    - prototype properties/methods can be overwritten which can break your code

* What is the difference between `==` and `===`?
  - `==` is the abstract equality operator that will compare for equality after doing any necessary type conversions.
  - `===` is the strict equality operator which will check if the two valules are pointing to the same value in memory and will not do type conversion.

* Explain the same-origin policy with regards to JavaScript.
  - The same-origin policy prevents JavaScript from making requests across domain boundaries. An origin is defined as a combination of URI scheme, hostname, and port number. This policy prevents a malicious script on one page from obtaining access to sensitve data on another web page through that page's Document Object Model.

* Why is it called a Ternary operator, what does the word "Ternary" indicate?
  - "Ternary" indicates three, and a ternary expression accepts three operands, the test condition, the "then" expression and the "else" expression.

* What is strict mode? What are some of the advantages/disadvantages of using it?
  - 'use strict' is a statement used to enable strict mode to entire scripts or individual functions. Strict mode is a way to opt into a restricted variant of JavaScript.
  - Pros:
    - makes it impossible to accidentally create global variables
    - makes assignments which would otherwise silently fail to throw an exception
    - catches some common coding bloopers, throwing exceptions
    - disables features that are confusing or poorly thought out
  - Cons:
    - missing features that some developers might be used to
    - concatenation of scripts written in differnet strict modes might cause issues
    - slow development

* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
  - Some examples of langauges that compile to JavaScript include CoffeeScript, TypeScript, and Elm.
  - Pros:
    - Types: JS vaue typing and type guessing is a menace with a large code base. This is why TypeScript exists.
    - Features: JS evolves quite slowly in terms of browser implementation.
  - Cons:
    - requires a build/compile process as browsers only run JavaScript
    - Debugging can be a pain if your source maps do not map nicely
    - Depends on the language, but smaller community leads to less resources, tutorials, libraries, and tooling.

* What tools and techniques do you use debugging JavaScript code?
  - React: React DevTools
  - JavaScript: Chrome Devtools, console logs, debugger statement
  - Node: debugger

* Explain the difference between mutable and immutable objects.
  - A mutable object is an object whose state can be modified after it is created. An immutable object is an object whose state cannot be modified after it is created. Immutability is a core principle in funcitonal programming, and has lots to offer to object-oriented programs as well.
  * What is an example of an immutable object in JavaScript?
    - In JavaScript, some built-in types (numbers, strings) are immutable, but custom objects are generally mutable.
    - Some built-in immutable JavaScript objects are Math, Date.
  * What are the pros and cons of immutability?
    - Pros:
      - Easier change detection
      - No need to worry about modification of an object
      - Reuse the same object without needing to create a copy
      - Using libraries like ImmutableJS, objects are modified using structural sharing and less memory is needed for having multiple objects with similar structures.
  * How can you achieve immutability in your own code?
    - You can use libraires like ImmutableJS, mori, or immer
    - use const declarations
    - For mutating objects, use the spread operator, Object.assign, Array.concat() to create new objects instead of mutating the original object.

* Explain the difference between synchronous and asynchronous functions.
  - Synchronous functions are blocking while asynchronous functions are not. In synchronous functions, statements complete before the next statement is run. In this case, the program is evacuated exactly in order of the statements and execution of the program is paused if one of the statements take a very long time.
  - Asynchronous functions usually accept a callback as a parameter and execution continues on the next line immediately after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. Heavy duty operations such as loading data from a web server or querying a database should be done asynchronously so that the main thread can continue executing other operations instead of blocking until that long operation to comoplete.

* What is event loop?
  * What is the difference between call stack and task queue?
  - The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the task queue, a function is dequeued and pushed onto the call stack to be executed.

* What are the differences between variables created using `let`, `var` or `const`?
  - 3 main differences: scope, hoisting, and reassignment
  - Variables declared using the `var` keyword are scoped to the function in which they are created, or if created outisde of any function, to the global object.
  - `let` and `const` are block scoped, meaning they are only accessible within the nearest set of curly braces (function, if else block, or for loop)
  - `var` allows variables to be hoisted, meaning they can be referenced in code before they are declared. `let` and `const` will not allow this, instead throwing an error.
  - Redeclaring a variable with `var` will not throw an error, but `let` and `const` will.
  - `let` and `const` differ in that `let` allows reassigning the variable's value while `const` does not.

* What are the differences between ES6 class and ES5 function constructors?
  - ES5 constructors uses a pseudoclassical pattern.
  - ES6 uses the ES6 pattern where you initiallize the class using `class` and constructor function.
  - The main difference in the constructor comes when using inheritance.
    - ES5: you need to call constructor of superclass to initialize superclass-derived members and then set the prototype to be the superclass' prototype
    - ES6: extends from superclass and invoke super with the superclass' inputs.

* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
  - call back functions
  - methods for `this` to be lexically scoped, meaning it is bound to the enclosing scope which is different compared to regular functions where `this` is determined by the object calling it.

* What advantage is there for using the arrow syntax for a method in a constructor?
  - The main advantage of using an arrow function as a method inside a constructor is that the value of `this` gets set at the time of the function creation and can't change after that and is lexically scoped.

* What is the definition of a higher-order function?
  - Higher-order funciton is a function that either takes a function as a callback function or returns a function.
  - Examples are map, forEach, filter, reduce, bind

* Can you give an example for destructuring an object or an array?
  - Array destructuring:
    - const foo = [`one`, `two`, `three`];
    - const [one, two, three] = foo;
    - console.log(one) // one
    - console.log(two) // two
    - console.log(three) // three
    - can also swap values like [a, b] = [b, a]
  - Object Destructuring
    - const o = { p: 42, q: true };
    - const { p, q } = o;
    - console.log(p) // 42
    - console.log(q) // true

* Can you give an example of generating a string with ES6 Template Literals?
  - include variables in a string
  - create multi-line strings
  - use as a substitute for templating libraries for simple variable interpolations

* Can you give an example of a curry function and why this syntax offers an advantage?
  - Currying is a pattern where a function with more than one parameter is broken into multiple functions that, when called in series, will accumulate all of the required parameters one at a time. This technique can be useful for making code written in a funcitonal style easier to read and compose. It's important to note that for a function to be curried, it needs to start out as one function, then broken out into a sequence of functions that each accepts one parameter.

* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
  -

* How can you share code between files?
* Why you might want to create static class members?
* What is the difference between `while` and `do-while` loops in JavaScript?
* What is a promise? Where and how would you use promise?

## Coding questions
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* What will be returned by each of these?
```javascript
console.log("hello" || "world")
console.log("foo" && "bar")
```
* Write an immediately invoked function expression (IIFE)
