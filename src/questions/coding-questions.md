---
title: Coding Questions
layout: layouts/page.njk
permalink: /questions/coding-questions/index.html
---

Question: What is the value of `foo`?
```javascript
var foo = 10 + '20';
```
- 1020 as a string

Question: What will be the output of the code below?
```javascript
console.log(0.1 + 0.2 == 0.3);
```
- false because floating numbers can't store properly all decimal numbers, because they store stuff in binary. More of a general computer problem than a JS problem.

Question: How would you make this work?
```javascript
add(2, 5); // 7
add(2)(5); // 7
```
```javascript
function add(a) {
  return arguments.length > 1 ? a + arguments[1] : function addSecond(b) {
    return a + b;
  }
}
```

Question: What value is returned from the following statement?
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```
- 'goh angasal a m'i'

Question: What is the value of `window.foo`?
```javascript
( window.foo || ( window.foo = "bar" ) );
```
- 'bar'

Question: What is the outcome of the two alerts below?
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```
- "Hello World"
- error, bar is undefined

Question: What is the value of `foo.length`?
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```
- 2

Question: What is the value of `foo.x`?
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```
- {n: 2}

Question: What does the following code print?
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
Promise.resolve().then(function() {
  console.log('three');
})
console.log('four');
```
- 'one'
- 'four'
- 'three'
- 'two'
- task queue won't be emptied until microtask queue is emptied first, even if more microtasks are queued up after executing microtasks.
- most tasks go into the (macro) task queue, such as setTimeout, setInterval, etc. But things like Promises, queueMicrotask go to micro task queue.

Question: What is the difference between these four promises?
```javascript
doSomething().then(function () {
  return doSomethingElse();
});

doSomething().then(function () {
  doSomethingElse();
});

doSomething().then(doSomethingElse());

doSomething().then(doSomethingElse);
```
1. This executes doSomething(), then when it resolves, it executes doSomethingElse() and the resolved value of the promise chain is the resolved value of doSomethingElse().
2. Same as option 1, except the resolved value of the promise chain is undefined because there is no return value from the .then() handler. Any return value from doSomethingElse() is ignored.
3. This executes doSomething() and then, before doSomething() has resolved, it also executes doSomethingElse() and passes the return value from doSomethingElse() as the .then() handler. This is something you'd never want to do and is most likely a coding mistake unless doSomethingElse() returns a function to be used as the .then() handler.
4. This is the same option as option 1 except that the resolved value from doSomething() is passed as the first argument to doSomethingElse(val). This is structurally the same as this:
```javascript
doSomething().then(function(result) {return doSomethingElse(result)})
```

Question: What will the code below output to the console and why?
```javascript
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```
- false
- true
- "var a = b = 3" is shorthand for:
  - b = 3
  - var a = b

Question: Consider the two functions below. Will they both return the same thing? Why or why not?
```javascript
function foo1() {
  return {
      bar: "hello"
  };
}

function foo2() {
  return {
      bar: "hello"
  };
}
```
- No. The objects are identical but will be different objects in memory. foo1() === foo2() will result to false.
