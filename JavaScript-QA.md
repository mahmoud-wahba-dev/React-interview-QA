# Top 50 questions in JavaScript

## **1. What is event bubbling and how can it be prevented?**

Event bubbling is a mechanism in which an event that is triggered on a nested or child element will also trigger on its parent elements, propagating up the DOM tree.

For example, if you have a button inside a div, when you click on the button, the click event will first be triggered on the button itself, then it will propagate up to the enclosing div, and finally to any parent elements of the div.

To prevent event bubbling in JavaScript, you can use the `stopPropagation()` method on the event object. This method stops the event from propagating up the DOM tree.

For example:

```js
document.querySelector("button").addEventListener("click", function (event) {
  event.stopPropagation();
  // Event handling logic for the button click
});
```

In this example, calling `event.stopPropagation()` stops the click event from bubbling up beyond the button element.

## **2. Explain the difference between `undefined` and `null`.**

In JavaScript, `undefined` and `null` are both values that represent the absence of a value. However, they have different meanings.

`undefined` is a built-in value in JavaScript that represents an uninitialized or unassigned variable or property. It is also returned when a function does not have an explicit return statement, or when a non-existent object property is accessed.

For example:

```js
let x;
console.log(x); // Output: undefined

function foo() {}
console.log(foo()); // Output: undefined

const obj = {
  prop: "value",
};
console.log(obj.nonexistentProp); // Output: undefined
```

On the other hand, `null` is a value that represents a deliberate non-value or empty value. It is often used to indicate that a variable or object property should have no value.

For example:

```js
let y = null;
console.log(y); // Output: null

const obj = {
  prop: null,
};
console.log(obj.prop); // Output: null
```

While `undefined` indicates the absence of a value due to an error or oversight, `null` is used to explicitly signify that there is no value.

## **3. What is closure, and how can it be used?**

In JavaScript, a closure is a feature that allows a function to access variables in its outer lexical scope even after the outer function has returned. In other words, a closure gives a function access to the variables and parameters of its outer function and any functions defined within it.

A closure is created when a function is defined inside another function and references variables from the outer function's scope. The inner function can then be returned or passed as an argument to another function, carrying with it the reference to the outer function's variables.

Here's an example:

```js
function outer() {
  const x = 10;

  function inner() {
    console.log(x);
  }

  return inner;
}

const innerFunc = outer();

// The 'inner' function still has access to the 'x' variable
innerFunc(); // Output: 10
```

In this example, we define an outer function `outer` that defines a local variable `x` and returns the inner function `inner`. The inner function `inner` logs the value of `x`, which is defined in the outer function's scope.

We then call the outer function and assign the result to `innerFunc`. When we call `innerFunc()` later, it still has access to the `x` variable defined in the outer function's scope, even though the outer function has already returned.

Closures are often used to create private variables and functions in JavaScript, as well as to create function factories that generate new functions with different behavior based on their creation context.

## **4. Explain the concept of hoisting.**

Hoisting is a behavior in JavaScript in which variable and function declarations are moved to the top of their respective scopes, regardless of where they are declared. This means that variables and functions can be used before they are declared without raising a reference error.

However, it is important to note that only the declarations are hoisted, not the initializations or assignments. If a variable is declared using `var` or `let`, its initialization is undefined until a value is assigned to it.

Here is an example of hoisting:

```js
console.log(x); // Output: undefined
var x = 10;
```

In this example, we try to log the value of `x` before it is declared. However, because variable declarations are hoisted to the top of their scope, the code above is equivalent to:

```js
var x;
console.log(x); // Output: undefined
x = 10;
```

Similarly, function declarations are also hoisted to the top of their scope. For example:

```js
foo(); // Output: 'Hello!'

function foo() {
  console.log("Hello!");
}
```

In this example, we call the `foo` function before it is declared. However, because function declarations are hoisted, the code above is equivalent to:

```js
function foo() {
  console.log("Hello!");
}

foo(); // Output: 'Hello!'
```

It's important to understand hoisting when working with JavaScript, as it can sometimes lead to unexpected behavior if declarations are not properly scoped or initialized.

## **5. What is a promise, and how does it differ from a callback function?**

A promise is a feature in JavaScript that allows for asynchronous operations to be performed and handled more easily. A promise represents the eventual completion or failure of an asynchronous operation and can be used to handle the results when they become available.

In contrast, a callback function is a function that is passed as an argument to another function and is executed when the outer function has completed its task. Callbacks are often used in JavaScript to handle asynchronous operations such as AJAX requests or timeouts.

The main difference between promises and callbacks is that promises provide a cleaner and more structured way to handle asynchronous operations. Promises allow you to chain multiple asynchronous operations together, making them easier to manage and debug. Additionally, promises have built-in error handling through their rejection mechanism, which makes it easier to handle errors that may occur during asynchronous operations.

Here's an example of using a promise:

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Success!");
  }, 1000);
});

promise
  .then((result) => {
    console.log(result); // Output: 'Success!'
  })
  .catch((error) => {
    console.error(error);
  });
```

In this example, we create a new promise that resolves with the value `'Success!'` after a timeout of 1 second. We then use the `then()` method to handle the successful resolution of the promise and log the result to the console. We also use the `catch()` method to handle any errors that may occur during the execution of the promise.

In contrast, here's an example of using a callback function:

```js
function doSomething(callback) {
  setTimeout(() => {
    callback("Success!");
  }, 1000);
}

doSomething((result) => {
  console.log(result); // Output: 'Success!'
});
```

In this example, we define a function `doSomething` that takes a callback function as an argument and executes it after a timeout of 1 second. We call the `doSomething` function and pass in a callback function that logs the result to the console.

While both promises and callbacks can be used to handle asynchronous operations in JavaScript, promises offer a more structured and reliable way to handle these operations, especially when dealing with complex chains of asynchronous events.

## **6. What are higher-order functions, and give an example.**

In JavaScript, a higher-order function is a function that either takes one or more functions as arguments, or returns a function as its result. Higher-order functions are an important concept in functional programming, as they enable functional composition and abstraction.

Here's an example of a higher-order function:

```js
function multiplyBy(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplyBy(2);
console.log(double(5)); // Output: 10
```

In this example, we define a higher-order function `multiplyBy` that takes a `factor` argument and returns a new function that multiplies its argument by the `factor`. We then call `multiplyBy(2)` to obtain a new function that doubles its argument, which we assign to the constant `double`. Finally, we call `double(5)` to apply the function and obtain the result `10`.

Higher-order functions are used frequently in JavaScript, especially when working with arrays and other collections. For example, the built-in `Array.prototype.map()` method is a higher-order function that applies a function to each element of an array and returns a new array with the results:

```js
const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map((number) => number * 2);
console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
```

In this example, we use the `map()` method to create a new array `doubledNumbers` that contains the elements of the original `numbers` array multiplied by 2. The arrow function `(number) => number * 2` is a callback function that is passed to the `map()` method and applied to each element of the array.

## **7. What is the difference between `==` and `===` operators?**

In JavaScript, the `==` operator and `===` operator are used to compare values. However, they behave differently depending on the type of values being compared.

The `==` operator performs a loose equality comparison, which means that it attempts to convert the operands to a common type before comparing them. This can sometimes lead to unexpected results, especially when comparing values of different types.

For example:

```js
console.log(1 == "1"); // Output: true
console.log(true == 1); // Output: true
console.log(null == undefined); // Output: true
```

In these examples, the `==` operator performs type coercion to convert the operands to a common type before comparing them. This can lead to unexpected results, such as the first example where the number 1 is equal to the string '1'.

On the other hand, the `===` operator performs a strict equality comparison, which means that it does not perform type coercion and compares the values based on their type and value.

For example:

```js
console.log(1 === "1"); // Output: false
console.log(true === 1); // Output: false
console.log(null === undefined); // Output: false
```

In these examples, the `===` operator compares the values based on their type and value, rather than attempting to convert them to a common type. As a result, the comparisons return false.

In general, it is a good practice to use the `===` operator unless you have a specific reason to use the `==` operator and understand its behavior.

## **8. How can you clone an object in JavaScript?**

In JavaScript, there are several ways to clone an object. Here are three common approaches:

1.  Using the spread operator (`...`)

The spread operator can be used to create a shallow copy of an object. This approach creates a new object that has the same properties and values as the original object.

```js
const originalObj = { a: 1, b: 2 };
const clonedObj = { ...originalObj };

console.log(clonedObj); // Output: {a: 1, b: 2}
```

Note that this approach only creates a shallow copy of the object, which means that any nested objects or arrays will still reference the same memory location as the original object.

2.  Using `Object.assign()`

The `Object.assign()` method can also be used to create a shallow copy of an object. This method copies the enumerable own properties from one or more source objects to a target object, and returns the target object.

```js
const originalObj = { a: 1, b: 2 };
const clonedObj = Object.assign({}, originalObj);

console.log(clonedObj); // Output: {a: 1, b: 2}
```

Note that like the spread operator approach, `Object.assign()` only creates a shallow copy of the object.

3.  Using `JSON.stringify()` and `JSON.parse()`

This approach can be used to create a deep copy of an object, including nested objects or arrays. However, it has some limitations, such as not being able to clone functions or non-enumerable properties.

```js
const originalObj = { a: 1, b: { c: 2 } };
const clonedObj = JSON.parse(JSON.stringify(originalObj));

console.log(clonedObj); // Output: {a: 1, b: {c: 2}}
```

This approach first converts the object to a JSON-formatted string using `JSON.stringify()`, and then parses the string back into an object using `JSON.parse()`. The resulting object is a deep copy of the original object.

Keep in mind that while these techniques are useful for cloning objects, they may have limitations depending on the specific use case.

## **9. How does the `this` keyword work in JavaScript?**

The `this` keyword in JavaScript refers to the current execution context or scope, which can vary depending on how a function is called. Understanding how `this` works is important for writing effective and maintainable JavaScript code.

Here's an overview of how `this` works in different situations:

1.  Global Scope

In the global scope (i.e., outside of any function), `this` refers to the global object, which is usually the `window` object in web browsers or the `global` object in Node.js.

```js
console.log(this); // Output: Window (in browser) or global (in Node.js)
```

2.  Function Scope

In a regular function (not an arrow function), the value of `this` depends on how the function is called.

If the function is called as a method of an object, `this` will refer to the object that the method is called on:

```js
const obj = {
  foo() {
    console.log(this);
  },
};

obj.foo(); // Output: {foo: ƒ} (the obj object)
```

If the function is called without an explicit owner object, `this` will refer to the global object.

```js
function foo() {
  console.log(this);
}

foo(); // Output: Window (in browser) or global (in Node.js)
```

If the function is called with the `new` keyword to create a new object, `this` will refer to the newly created object.

```js
function Person(name) {
  this.name = name;
  this.sayHello = function () {
    console.log(`Hello, my name is ${this.name}`);
  };
}

const person = new Person("John");
person.sayHello(); // Output: 'Hello, my name is John'
```

3.  Arrow Functions

In an arrow function, `this` is lexically scoped, which means that it inherits the value of `this` from its parent scope.

```js
const obj = {
  foo() {
    const bar = () => {
      console.log(this);
    };
    bar();
  },
};

obj.foo(); // Output: {foo: ƒ} (the obj object)
```

Note that arrow functions do not have their own `this` value, so they cannot be used as constructors and should not be used in situations where dynamic `this` binding is required.

4.  Using `call()`, `apply()`, and `bind()`

You can also use the `call()`, `apply()`, and `bind()` methods to explicitly set the value of `this` when calling a function.

```js
function foo() {
  console.log(this);
}

const obj = { name: "John" };

// Using call()
foo.call(obj); // Output: {name: 'John'}

// Using apply()
foo.apply(obj); // Output: {name: 'John'}

// Using bind()
const boundFoo = foo.bind(obj);
boundFoo(); // Output: {name: 'John'}
```

In these examples, we are using the `call()`, `apply()`, and `bind()` methods to set the value of `this` to the `obj` object when calling the `foo()` function.

In summary, the behavior of `this` in JavaScript can be challenging to understand, but it is crucial for writing effective and maintainable code. By understanding the different ways that `this` can be used, you can write more robust and flexible code that takes advantage of the full power of the language.

## **10. Explain the difference between `let`, `const` and `var`.**

In JavaScript, `let`, `const`, and `var` are used to declare variables. While they share some similarities, there are some key differences between them.

`var`:

`var` is the oldest way of declaring variables in JavaScript. It is function-scoped, which means that a variable declared with `var` exists throughout the entire function it is declared in, regardless of block scope.

```js
function exampleFunction() {
  var x = 5;
  if (true) {
    var x = 10; // same variable as above
  }
  console.log(x); // Output: 10
}
```

In this example, the variable `x` is declared with `var`. Even though it is redeclared inside the `if` block, it still refers to the same variable outside the block.

One of the downsides of using `var` is that it can be easily overwritten or reassigned, which can lead to unexpected behavior.

`let`:

Introduced in ECMAScript 6, `let` is block-scoped, which means that a variable declared with `let` only exists within the block it is declared in.

```js
function exampleFunction() {
  let x = 5;
  if (true) {
    let x = 10; // different variable than above
  }
  console.log(x); // Output: 5
}
```

In this example, the variable `x` is declared with `let`. The inner `x` variable declared inside the `if` block is a separate variable from the outer `x` variable.

Unlike `var`, `let` cannot be redeclared in the same scope, which helps prevent errors and make code easier to reason about.

`const`:

Similar to `let`, `const` is also block-scoped. However, while `let` allows you to assign a new value to a variable, `const` does not. Once a variable is declared with `const`, its value cannot be changed.

```js
const x = 5;
x = 10; // Error: Assignment to constant variable.
```

In this example, we attempt to assign a new value to a variable declared with `const`, which results in an error.

`const` is useful when you need to declare a variable that should not be changed, such as a constant or a configuration object.

In summary, `var` is function-scoped and can be easily overwritten, `let` is block-scoped and cannot be redeclared, and `const` is block-scoped and cannot be reassigned after declaration. Choosing the appropriate variable declaration method depends on your specific use case and coding style preferences.

## **11. What is a generator function?**

In JavaScript, a generator function is a special type of function that allows you to define an iterative algorithm by writing code that can be paused and resumed at any point.

Generator functions are defined using the `function*` syntax, and use the `yield` keyword to produce a sequence of values. When a generator function is called, it returns a generator object that can be used to iterate over the sequence of values produced by the function, one at a time.

Here's an example of a simple generator function:

```js
function* generateSequence() {
  yield 1;
  yield 2;
  yield 3;
}

const sequence = generateSequence();

console.log(sequence.next().value); // Output: 1
console.log(sequence.next().value); // Output: 2
console.log(sequence.next().value); // Output: 3
```

In this example, we define a generator function `generateSequence` that yields the values `1`, `2`, and `3`. We then create a generator object `sequence` by calling `generateSequence()`, and use the `next()` method to iterate over the sequence of values produced by the generator.

Each call to `next()` returns an object with two properties: `value`, which contains the current value produced by the generator, and `done`, which is a boolean indicating whether the end of the generator sequence has been reached.

Generator functions are useful in a variety of situations, such as generating sequences of numbers or strings, iterating over large data sets, and implementing asynchronous programming patterns.

One of the key benefits of generator functions is that they allow for lazy evaluation of sequences, which means that only the values that are needed at any given time are computed, rather than computing an entire sequence upfront. This can help improve performance and reduce memory usage in certain situations.

## **12. What is the difference between synchronous and asynchronous code?**

In JavaScript, synchronous and asynchronous code refer to different ways of executing code.

Synchronous code is executed sequentially, one statement at a time. When a statement is executed, the program waits for it to complete before moving on to the next statement. Synchronous code blocks the execution thread until it completes, meaning that the program can't do anything else while that code is running.

For example:

```js
console.log("First");
console.log("Second");
console.log("Third");
```

In this example, the three `console.log()` statements are executed synchronously, in order from first to third.

Asynchronous code, on the other hand, allows the program to execute multiple operations at the same time without blocking the execution thread. In asynchronous code, when an operation is started, the program continues to run without waiting for the operation to complete. The result of the operation is handled by a callback function or a promise, which is executed when the operation is finished.

For example:

```js
console.log("First");
setTimeout(() => console.log("Second"), 1000);
console.log("Third");
```

In this example, the first and third `console.log()` statements are executed synchronously. However, the second `console.log()` statement is executed asynchronously, using the `setTimeout()` function to delay its execution by one second. During that one second delay, the program continues to run and executes the third `console.log()` statement. After one second has passed, the `setTimeout()` callback function is executed, outputting 'Second' to the console.

Asynchronous code is useful when working with I/O operations, such as reading from a file or making an API call, or when performing long-running computations that could block the execution thread. By using asynchronous code, the program can continue to respond to user input or perform other tasks while these operations are being processed.

In summary, synchronous code blocks the execution thread until it completes, while asynchronous code allows multiple operations to be executed simultaneously without blocking the execution thread.

## **13. What are the different ways to declare a function in JavaScript?**

In JavaScript, there are several ways to declare a function. Here are four common approaches:

1.  Function declaration

A function declaration is the most common way to define a function in JavaScript. It uses the `function` keyword followed by an optional function name, a list of parameters enclosed in parentheses, and a block of statements enclosed in curly braces.

```js
function add(a, b) {
  return a + b;
}
```

2.  Function expression

A function expression defines a function as a value of a variable. It uses the `function` keyword followed by an optional function name, a list of parameters enclosed in parentheses, and a block of statements enclosed in curly braces. The function is then assigned to a variable using the `=` operator.

```js
const add = function (a, b) {
  return a + b;
};
```

3.  Arrow function

Introduced in ECMAScript 6, an arrow function provides a concise syntax for defining a function. It uses the `=>` operator to separate the list of parameters from the function body, which can be either a single expression or a block of statements enclosed in curly braces.

```js
const add = (a, b) => a + b;
```

4.  Function constructor

While not commonly used, it is also possible to create a function using the `Function` constructor. This approach takes a comma-separated list of arguments followed by the function body as string arguments.

```js
const add = new Function("a", "b", "return a + b");
```

Note that this approach can be less efficient and potentially unsafe if the function body is taken from an external source.

In summary, there are multiple ways to declare a function in JavaScript, including function declaration, function expression, arrow function, and function constructor. Which approach you choose depends on your specific use case and coding style preference.

## **14. Explain the difference between `map`, `filter` and `reduce`.**

In JavaScript, `map`, `filter`, and `reduce` are three higher-order array methods that allow you to perform common operations on arrays in a concise and functional way.

1.  `map()`

The `map()` method creates a new array by calling a function on each element of the original array and returning an array of the same length, with each element transformed by the function.

```js
const numbers = [1, 2, 3, 4];
const doubledNumbers = numbers.map((num) => num * 2);
console.log(doubledNumbers); // Output: [2, 4, 6, 8]
```

In this example, the `map()` method is called on the `numbers` array, which returns a new array containing each element of the `numbers` array multiplied by 2.

2.  `filter()`

The `filter()` method creates a new array by calling a function on each element of the original array and returning an array of elements that pass a certain condition based on the logic in the function provided.

```js
const numbers = [1, 2, 3, 4];
const evenNumbers = numbers.filter((num) => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]
```

In this example, the `filter()` method is called on the `numbers` array, which filters out any elements that are not even numbers.

3.  `reduce()`

The `reduce()` method applies a function to each element of an array and reduces the array to a single value. The function takes two arguments: an accumulator and the current element, and returns the updated accumulator.

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);
console.log(sum); // Output: 10
```

In this example, the `reduce()` method is called on the `numbers` array, which adds up all the elements of the array to produce a single value.

In summary, `map()` transforms each element in an array and returns a new array, `filter()` selects and returns elements that meet a certain condition, and `reduce()` applies a function to each element and reduces the array to a single value. These methods are powerful tools for working with arrays and can make your code more concise and expressive.

## **15. What is memoization in JavaScript?**

Memoization is a technique used to optimize the performance of functions by caching the results of expensive function calls and returning the cached result when the same inputs occur again.

In JavaScript, memoization can be implemented using closures. The basic idea is to create a closure that contains a cache object. The closure returns a function that checks if the requested input has already been cached, and returns the cached result if it exists. If the input has not yet been cached, the closure calls the original function with the input parameter, caches the result, and returns the result.

Here's an example of how to implement memoization:

```js
function memoize(func) {
  const cache = {};
  return function (...args) {
    const key = JSON.stringify(args);
    if (cache[key]) {
      console.log("Returning from cache:", cache[key]);
      return cache[key];
    }
    const result = func.apply(this, args);
    console.log("Adding to cache:", result);
    cache[key] = result;
    return result;
  };
}

// Example function to be memoized
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

const memoizedFibonacci = memoize(fibonacci);

console.log(memoizedFibonacci(10)); // Output: 55
console.log(memoizedFibonacci(10)); // Output: Returning from cache: 55
```

In this example, we define a `memoize()` function that takes a function as an argument and returns a closure that implements memoization. When the returned function is called with a set of arguments, the closure checks if the arguments have already been cached. If so, the cached result is returned. Otherwise, the function passed to `memoize()` is called with the input parameters, the result is cached, and the result is returned.

We then define a `fibonacci()` function, which calculates the nth Fibonacci number recursively. We use `memoize()` to create a new function `memoizedFibonacci` that caches the results of previous calculations, improving performance for repeated calculations.

In summary, memoization is a powerful technique for optimizing the performance of functions in JavaScript by caching the results of expensive function calls and returning the cached result when the same inputs occur again.

## **16. What is the difference between `apply()` and `call()`?**

In JavaScript, both `call()` and `apply()` are methods that allow you to call a function with a specified `this` value and arguments. The main difference between the two methods is how they pass arguments to the function being called.

1.  `call()`

The `call()` method is used to invoke a function with a specified `this` value and arguments provided individually. The first argument of `call()` is the `this` value to be used inside the function, while any additional arguments are provided as separate arguments.

For example:

```js
function greet(name) {
  console.log(`Hello, ${name}! My name is ${this.name}.`);
}

const person = { name: "John" };

greet.call(person, "Alice"); // Output: "Hello, Alice! My name is John."
```

In this example, we use the `call()` method to invoke the `greet()` function with `person` as the `this` value, and pass the argument `'Alice'`.

2.  `apply()`

The `apply()` method is similar to `call()`, but it takes the function arguments in the form of an array or an array-like object. The first argument of `apply()` is the `this` value to be used inside the function, while the second argument is an array or an array-like object containing the function arguments.

For example:

```js
function sum(a, b, c) {
  return a + b + c;
}

const numbers = [1, 2, 3];

const result = sum.apply(null, numbers); // equivalent to sum(1, 2, 3)

console.log(result); // Output: 6
```

In this example, we use the `apply()` method to invoke the `sum()` function with `null` as the `this` value, and pass the `numbers` array as the second argument.

In summary, both `call()` and `apply()` allow you to call a function with a specified `this` value and arguments, but `call()` passes arguments individually, while `apply()` takes the arguments as an array or an array-like object.

## **17. What is the purpose of the `use strict` directive?**

The "use strict" directive is a feature introduced in ECMAScript 5 (ES5) that allows you to place your code in a "strict mode". It is used to enforce stricter parsing and error handling rules in JavaScript.

When you add the "use strict" directive at the beginning of a script or a function, it enables a set of new language features and disallows certain actions that were previously allowed. This helps to prevent common mistakes and improve the overall quality of your code.

Some of the benefits of using "use strict" include:

1.  Preventing the use of undeclared variables

In non-strict mode, if you assign a value to an undeclared variable, it will be implicitly created as a global variable. In strict mode, however, you will get a reference error if you try to access an undeclared variable.

2.  Disallowing duplicate property names in objects

In non-strict mode, if you define two properties with the same name in an object literal, the second property overwrites the first without any errors. In strict mode, however, you will get a syntax error if you try to define duplicate property names.

3.  Making `eval()` safer

In non-strict mode, the `eval()` function can execute any code passed to it, including potentially harmful code. In strict mode, however, `eval()` creates a new scope and disallows access to the variable environment of the caller.

Here's an example of how to use the "use strict" directive in a script:

```js
"use strict";

function sum(a, b) {
  return a + b;
}

console.log(sum(1, 2));
```

In this example, we enable strict mode by adding the "use strict" directive at the top of the script. Any code inside the `sum()` function will also run in strict mode, since it is enclosed in the same script.

In summary, the "use strict" directive is a way to opt in to stricter parsing and error handling rules in JavaScript, which can help prevent common mistakes and improve the overall quality of your code.

## **18. Explain the difference between prototypal and classical inheritance.**

In JavaScript, there are two different ways to implement inheritance: prototypal and classical inheritance.

1.  Prototypal Inheritance

Prototypal inheritance is based on the prototype chain, which allows objects to inherit properties and methods from other objects. Every object in JavaScript has a prototype, which is another object that it inherits from.

Here's an example of how to implement prototypal inheritance:

```js
// Define a parent object
const person = {
  name: "John",
  age: 30,
  greet() {
    console.log(
      `Hello, my name is ${this.name} and I'm ${this.age} years old.`
    );
  },
};

// Define a child object that inherits from the parent object
const student = Object.create(person);
student.major = "Computer Science";
student.greet(); // Output: "Hello, my name is John and I'm 30 years old."
```

In this example, we define a `person` object that has a `name`, `age`, and a `greet()` method. We then create a new `student` object using the `Object.create()` method, which sets the `student` object's prototype to be the `person` object. The `student` object also has a `major` property that is specific to the `student` object. When we call the `greet()` method on the `student` object, it uses the `greet()` method of the `person` object through prototypal inheritance.

2.  Classical Inheritance

Classical inheritance is based on the concept of classes and objects. This approach emphasizes the distinction between classes (which define the properties and methods of an object) and instances (which are the actual objects themselves).

Here's an example of how to implement classical inheritance in JavaScript using constructor functions:

```js
// Define a parent class
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(
      `Hello, my name is ${this.name} and I'm ${this.age} years old.`
    );
  }
}

// Define a child class that inherits from the parent class
class Student extends Person {
  constructor(name, age, major) {
    super(name, age);
    this.major = major;
  }
}

// Create a new student object
const student = new Student("John", 30, "Computer Science");
student.greet(); // Output: "Hello, my name is John and I'm 30 years old."
```

In this example, we define a `Person` class using the `class` syntax, which has a `name`, `age`, and a `greet()` method. We then define a `Student` class that inherits from the `Person` class using the `extends` keyword. The `Student` class has a `major` property that is specific to the `Student`. We then create a new `student` object using the `new` operator and pass in the required parameters to the `Student` class constructor. When we call the `greet()` method on the `student` object, it uses the `greet()` method of the `Person` class through classical inheritance.

In summary, prototypal inheritance is based on the prototype chain and allows objects to inherit properties and methods from other objects, while classical inheritance is based on the concept of classes and emphasizes the distinction between classes and instances. Both approaches can be used to implement inheritance in JavaScript, depending on your coding style preference and project requirements.

## **19. What is currying, and how can it be used in JavaScript?**

Currying is a functional programming technique that involves transforming a function with multiple arguments into a sequence of nested functions, each taking a single argument. The result is a new function that can be called with one argument at a time, and returns a new function that expects the next argument.

In JavaScript, currying can be achieved using closures. Here's an example of how to implement currying in JavaScript:

```js
function add(a) {
  return function (b) {
    return a + b;
  };
}

const addFive = add(5);
console.log(addFive(3)); // Output: 8
```

In this example, we define a `add()` function that takes a single argument `a` and returns another function that takes a single argument `b`. This returned function adds `a` and `b` together and returns the result.

We then call the `add()` function with the value `5`, which returns a new function that adds `5` to any number passed to it. We store this new function in the `addFive` variable. Finally, we call the `addFive()` function with the value `3`, which returns `8`.

Currying has several benefits, including:

1.  Partial application: Curried functions can be partially applied by passing some of the arguments upfront, which creates a new function that expects the remaining arguments. This can make your code more flexible and reusable.
2.  Enhancing code readability: Currying can make complex functions easier to read and understand, especially when dealing with long chains of functions that take many arguments.
3.  Composition: Curried functions can be easily composed with other functions to create more complex functions, which helps to promote modularity and reusability in your code.

Here's an example of partial application using currying:

```js
function multiply(a) {
  return function (b) {
    return a * b;
  };
}

const double = multiply(2);
console.log(double(5)); // Output: 10
```

In this example, we define a `multiply()` function that takes a single argument `a` and returns another function that takes a single argument `b`. This returned function multiplies `a` and `b` together and returns the result.

We then call the `multiply()` function with the value `2`, which returns a new function that multiplies any number passed to it by `2`. We store this new function in the `double` variable. Finally, we call the `double()` function with the value `5`, which returns `10`.

In summary, currying is a functional programming technique that involves transforming a function with multiple arguments into a sequence of nested functions, each taking a single argument. It can be used in JavaScript to increase code flexibility, enhance readability, and promote composition.

## **20. Explain how the `typeof` operator works.**

In JavaScript, the `typeof` operator is used to determine the data type of a value or expression. It returns a string that indicates the data type of the operand.

Here are the basic rules for using the `typeof` operator:

1.  If the operand is a number, the `typeof` operator returns "number".
2.  If the operand is a string, the `typeof` operator returns "string".
3.  If the operand is a boolean value, the `typeof` operator returns "boolean".
4.  If the operand is `undefined`, the `typeof` operator returns "undefined".
5.  If the operand is `null`, the `typeof` operator returns "object". This is actually a bug in the language that has persisted since the beginning.
6.  If the operand is an object or an array, the `typeof` operator returns "object".
7.  If the operand is a function, the `typeof` operator returns "function".

Here are some examples of using the `typeof` operator in JavaScript:

```js
console.log(typeof 123); // Output: "number"
console.log(typeof "hello"); // Output: "string"
console.log(typeof true); // Output: "boolean"
console.log(typeof undefined); // Output: "undefined"
console.log(typeof null); // Output: "object"
console.log(typeof {}); // Output: "object"
console.log(typeof []); // Output: "object"
console.log(typeof function () {}); // Output: "function"
```

In summary, the `typeof` operator is used to determine the data type of a value or expression in JavaScript. It returns a string that indicates the data type of the operand, such as "number", "string", "boolean", "undefined", "object", or "function".

## **21. What is the difference between the `push()` and `pop()` methods?**

In JavaScript, the `push()` and `pop()` methods are used to manipulate arrays.

1.  `push()`: The `push()` method adds one or more elements to the end of an array and returns the new length of the array.

Here's an example of how to use the `push()` method:

```js
const arr = [1, 2, 3];
arr.push(4);
console.log(arr); // Output: [1, 2, 3, 4]
```

In this example, we define an array `arr` with three elements. We then call the `push()` method on `arr` and pass in the value `4`. The `push()` method adds `4` to the end of the `arr` array and returns the new length of the array. Finally, we log the `arr` array to the console, which outputs `[1, 2, 3, 4]`.

Under the hood, the `push()` method works by modifying the original array in place. It increases the length of the array by one and adds the new element(s) to the end.

2.  `pop()`: The `pop()` method removes the last element from an array and returns the removed element.

Here's an example of how to use the `pop()` method:

```js
const arr = [1, 2, 3];
const lastElement = arr.pop();
console.log(lastElement); // Output: 3
console.log(arr); // Output: [1, 2]
```

In this example, we define an array `arr` with three elements. We then call the `pop()` method on `arr`, which removes the last element (`3`) from the array and returns it. We store the removed element in the `lastElement` variable. Finally, we log `lastElement` and the modified `arr` array to the console, which outputs `3` and `[1, 2]`, respectively.

Under the hood, the `pop()` method works by modifying the original array in place. It removes the last element from the array and decreases the length of the array by one.

In summary, the `push()` and `pop()` methods are used to manipulate arrays in JavaScript. The `push()` method adds one or more elements to the end of an array, while the `pop()` method removes the last element from an array. Both methods modify the original array in place and return a value that reflects the modification.

## **22. What is a ternary operator in JavaScript?**

In JavaScript, a ternary operator is a shorthand conditional statement used to evaluate a Boolean expression and return one of two values depending on whether the expression evaluates to true or false. The syntax of the ternary operator is as follows:

```js
condition ? value1 : value2;
```

If the condition is true, the expression will evaluate to `value1`, otherwise it will evaluate to `value2`. Here's an example:

```js
var x = 5;
var result = x > 10 ? "x is greater than 10" : "x is less than or equal to 10";
console.log(result); // Output: "x is less than or equal to 10"
```

In this example, the condition `x > 10` evaluates to false, so the expression returns the string "x is less than or equal to 10".

## **23. What is the difference between a shallow copy and a deep copy of an object?**

In JavaScript, when you create a copy of an object, you can create either a shallow copy or a deep copy. The main difference between the two is how they handle nested objects and arrays.

A shallow copy creates a new object that references the same memory locations as the original object. This means that any changes made to the original object will also affect the shallow copy, and vice versa. However, if the original object contains nested objects or arrays, the references to those nested objects and arrays are copied over, but the nested objects and arrays themselves are not duplicated. Instead, the shallow copy will reference the same nested objects and arrays as the original object.

Here's an example:

```js
var originalObj = { a: 1, b: { c: 2 } };
var shallowCopy = Object.assign({}, originalObj);

originalObj.b.c = 3;

console.log(originalObj); // Output: { a: 1, b: { c: 3 } }
console.log(shallowCopy); // Output: { a: 1, b: { c: 3 } }
```

In this example, when we change the value of `b.c` in the original object, the same change is reflected in the shallow copy because they both reference the same nested object `{ c: 3 }`.

On the other hand, a deep copy creates a new object with all the same properties and values as the original object, including any nested objects or arrays. This means that changes made to the original object will not affect the deep copy, and vice versa.

Here's an example:

```js
var originalObj = { a: 1, b: { c: 2 } };
var deepCopy = JSON.parse(JSON.stringify(originalObj));

originalObj.b.c = 3;

console.log(originalObj); // Output: { a: 1, b: { c: 3 } }
console.log(deepCopy); // Output: { a: 1, b: { c: 2 } }
```

In this example, when we change the value of `b.c` in the original object, the deep copy remains unchanged because it copied all the nested objects and arrays by value, rather than by reference.

## **24. What is the event loop in JavaScript, and how does it work?**

In JavaScript, the event loop is a mechanism that handles asynchronous callbacks and manages the order in which they are executed. When an event occurs (like a user clicking a button or a response coming back from a server), a callback function is created and added to a task queue. The event loop continuously checks the call stack for any running functions or synchronous code, and when it's empty, it moves on to process tasks in the task queue.

Here's how the event loop works:

1.  All synchronous code gets executed immediately and the results are returned.
2.  Any asynchronous code (like setTimeout or AJAX requests) creates a callback function and adds it to the task queue.
3.  When the call stack is empty (i.e., all synchronous code has been executed), the event loop takes the first task from the task queue and pushes its corresponding callback function onto the call stack to be executed.
4.  This process repeats, with the event loop continuously checking the call stack for any running functions or synchronous code and moving on to process tasks in the task queue when it's empty.

To illustrate this, consider the following example:

```js
console.log("start");

setTimeout(function () {
  console.log("middle");
}, 2000);

console.log("end");
```

Even though `setTimeout` is called second, it is an asynchronous function that creates a callback and adds it to the task queue. So the output of this example will be:

```js
start;
end;
middle;
```

This is because the two `console.log` statements are synchronous and get executed immediately, whereas the callback function for `setTimeout` is added to the task queue and only gets executed after a delay of 2 seconds.

The event loop is what makes it possible to write non-blocking code in JavaScript, as it allows the program to continue running while waiting for asynchronous operations to complete.

## **25. What is the difference between a module and a script in JavaScript?**

In JavaScript, a module is a reusable piece of code that encapsulates related functionality and can be imported into other modules or scripts, whereas a script is a standalone program written in JavaScript that runs in the context of a web page.

Here are some key differences between modules and scripts:

1.  Scope: Modules have their own scope, which means that variables and functions defined inside a module are not visible outside of that module unless explicitly exported. Scripts, on the other hand, have access to the global scope of the web page they're running in, which means that any variables or functions defined in a script can be accessed globally.
2.  Reusability: Modules are designed to be reusable, which means that they can be imported into other modules or scripts as needed. This allows developers to build complex applications by breaking them down into smaller, more manageable modules. Scripts, on the other hand, are typically standalone programs that are run once and discarded.
3.  Exporting: In order for a module to expose its functionality to other modules or scripts, it must explicitly export the relevant functions or variables using the `export` keyword. Scripts do not need to export anything, as all of their functionality is accessible globally by default.
4.  Loading: Modules are loaded asynchronously, which means that they are only executed when they are imported by another module or script. Scripts, on the other hand, are loaded synchronously, which means that they are executed as soon as they are encountered in the HTML document.

Overall, modules are designed to promote code reuse, modularity, and maintainability, while scripts are designed to provide standalone functionality within the context of a web page.

## **26. What is the difference between `setTimeout()` and `setInterval()`?**

In JavaScript, both `setTimeout()` and `setInterval()` are used to execute a function after a certain amount of time has elapsed. However, there are some key differences between the two:

`setTimeout()`: This function allows you to schedule a function to run once after a specified amount of time has elapsed. The function will only be executed once, unless you call `setTimeout()` again.

Here's an example that executes a function after a delay of 2 seconds:

```js
setTimeout(function () {
  console.log("Hello, world!");
}, 2000);
```

`setInterval()`: This function allows you to schedule a function to run repeatedly at a given interval (i.e., every x milliseconds). The function will continue to execute until you call `clearInterval()`.

Here's an example that executes a function every second:

```js
var count = 0;
var intervalId = setInterval(function () {
  console.log(count++);
}, 1000);
```

In this example, we set up a variable `count` and increment it inside the callback function. We also store the return value of `setInterval()` in a variable called `intervalId`. This allows us to stop the interval later by calling `clearInterval(intervalId)`.

So, in summary:

- `setTimeout()` runs a function once after a specified amount of time has elapsed.
- `setInterval()` runs a function repeatedly at a given interval, until stopped with `clearInterval()`.

## **27. Explain what the `delete` operator does.**

In JavaScript, the `delete` operator is used to remove a property from an object. The syntax for using the `delete` operator is as follows:

```js
delete objectName.propertyName;
```

Here's an example:

```js
var obj = { a: 1, b: 2 };
delete obj.a;
console.log(obj); // Output: { b: 2 }
```

In this example, we created an object `obj` with two properties `a` and `b`. We then used the `delete` operator to remove the `a` property from the object. When we log the object to the console, we see that only the `b` property remains.

It's worth noting that the `delete` operator does not affect variables or functions. It can only be used to remove properties from objects. Additionally, if you try to delete a non-existent property or a property that is part of the object's prototype chain (i.e., inherited from a parent object), the `delete` operator will return `true`, but it will have no effect.

Here's an example of deleting a non-existent property:

```js
var obj = { a: 1 };
console.log(delete obj.b); // Output: true
console.log(obj); // Output: { a: 1 }
```

In this example, we tried to delete a non-existent property `b` from the object `obj`. The `delete` operator returns `true`, indicating that the operation was successful, but since the property doesn't exist in the first place, the object remains unchanged.

## **28. What is the difference between `Object.keys()` and `Object.getOwnPropertyNames()`?**

In JavaScript, `Object.keys()` and `Object.getOwnPropertyNames()` are both used to retrieve the property names of an object. However, there are some key differences between the two:

1.  Prototype chain: `Object.keys()` returns only the enumerable properties that are directly defined on the object itself, not those inherited from its prototype chain. `Object.getOwnPropertyNames()`, on the other hand, returns all property names, including non-enumerable ones and those inherited from prototypes.

Here's an example to illustrate the difference:

```js
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function () {
  console.log("Hello, " + this.name + "!");
};

var john = new Person("John");

console.log(Object.keys(john)); // Output: ["name"]
console.log(Object.getOwnPropertyNames(john)); // Output: ["name", "constructor", "sayHello"]
```

In this example, we create a `Person` constructor function with a `name` property and a `sayHello()` method added to its prototype. We then create a new object `john` using this constructor function. When we call `Object.keys(john)`, we see that it only returns the enumerable `name` property directly defined on `john`. However, when we call `Object.getOwnPropertyNames(john)`, we see that it returns all properties, including the non-enumerable `constructor` property and the inherited `sayHello()` method.

2.  Array-like object: `Object.keys()` works only with objects that have enumerable properties (i.e., plain objects or objects created with `Object.create(null)`), whereas `Object.getOwnPropertyNames()` works with any object that has properties.

Here's an example to illustrate the difference:

```js
var arr = ["a", "b", "c"];

console.log(Object.keys(arr)); // Output: ["0", "1", "2"]
console.log(Object.getOwnPropertyNames(arr)); // Output: ["0", "1", "2", "length"]
```

In this example, `arr` is an array-like object with three elements. When we call `Object.keys(arr)`, we see that it returns an array of stringified indices ("0", "1", "2"), which are the enumerable properties of the object. However, when we call `Object.getOwnPropertyNames(arr)`, we see that it also returns the non-enumerable `length` property of the object.

Overall, `Object.keys()` and `Object.getOwnPropertyNames()` are similar in that they both return property names, but they differ in their handling of non-enumerable properties and inherited properties, as well as their compatibility with different types of objects.

## **29. What is a decorator in JavaScript?**

In JavaScript, a decorator is a function that takes another function or class as input and extends or modifies its behavior without changing its source code. Decorators are typically used to add functionality such as logging, caching, or validation to existing functions or classes, or to modify their behavior based on certain conditions.

Decorators can be applied using the `@` symbol followed by the name of the decorator function, like this:

```js
@decorator
function myFunction() {
  // ...
}
```

Or for classes:

```js
@decorator
class MyClass {
  // ...
}
```

Here's an example of a simple decorator that logs the arguments and return value of a function:

```js
function log(target, name, descriptor) {
  var original = descriptor.value;
  descriptor.value = function () {
    console.log("Arguments:", arguments);
    var result = original.apply(this, arguments);
    console.log("Result:", result);
    return result;
  };
  return descriptor;
}

class MyClass {
  @log
  myMethod(a, b) {
    return a + b;
  }
}

var obj = new MyClass();
obj.myMethod(1, 2); // Output: Arguments: [1, 2], Result: 3
```

In this example, we define a `log` decorator function that wraps a method with logging statements. We then decorate the `myMethod()` method inside the `MyClass` class with the `@log` decorator. When we create a new object of the `MyClass` class and call its `myMethod()` method, we see that the arguments and return value are logged to the console.

Decorators are implemented using either classes or higher-order functions in JavaScript, depending on the use case. With classes, decorators are called automatically when the class is defined, whereas with higher-order functions, the decorator needs to be explicitly called to wrap the target function.

## **30. Explain the difference between a reference type and a value type.**

In JavaScript, variables can be assigned either a value type or a reference type. The main difference between the two is how they are stored in memory and how they are passed around in the code.

Value types include primitive data types such as numbers, strings, booleans, null, and undefined. These types are stored directly in memory and each variable holds its own copy of the value. When one variable is assigned to another, a new copy of the value is created and assigned to the second variable. This means that changes made to one variable do not affect the other variable.

Here's an example:

```js
var x = 1;
var y = x;

x = 2;

console.log(x); // Output: 2
console.log(y); // Output: 1
```

In this example, we create a variable `x` with a value of `1`, and then assign its value to another variable `y`. We then change the value of `x` to `2`. When we log the values of `x` and `y` to the console, we see that `x` has changed to `2`, but `y` still has the original value of `1`.

Reference types, on the other hand, include objects, arrays, and functions. These types are stored in memory by reference, which means that when you assign a variable to an object, array, or function, you're actually assigning a reference to the location in memory where that value is stored. This means that both variables point to the same object in memory, so changes made to the object through one variable will be reflected in the other variable as well.

Here's an example:

```js
var obj1 = { x: 1 };
var obj2 = obj1;

obj1.x = 2;

console.log(obj1.x); // Output: 2
console.log(obj2.x); // Output: 2
```

In this example, we create an object `obj1` with a property `x` set to `1`, and then assign its reference to a new variable `obj2`. We then change the value of `x` to `2` using `obj1`. When we log the value of `x` for both `obj1` and `obj2`, we see that both have been updated to `2`.

In summary, the main difference between value types and reference types is how they are stored in memory and how they are passed around in the code. Value types are copied by value, while reference types are copied by reference.

## **31. What is the difference between anonymous and named functions?**

In JavaScript, functions can be defined in two ways: as anonymous functions and as named functions.

An anonymous function is a function without a name. It is typically defined using the function keyword followed by parentheses and then curly braces containing the function's code. For example:

```js
let anonymousFunction = function () {
  // Code for the function
};
```

A named function, on the other hand, is a function with a name. It is typically defined using the function keyword followed by the name of the function, parentheses, and then curly braces containing the function's code. For example:

```js
function namedFunction() {
  // Code for the function
}
```

The main difference between an anonymous and named function is that a named function can be called recursively, whereas an anonymous function cannot. This is because a named function has a reference to itself through its name, while an anonymous function does not.

Another difference between anonymous and named functions is that named functions are more useful when debugging code. When an error occurs in an anonymous function, it can be difficult to determine which function caused the error since it doesn't have a name. However, if the function is named, the error message will include the function's name, making it easier to debug the problem.

Overall, both anonymous and named functions have their uses in JavaScript development, and the choice between them depends on the specific needs of your code.

In terms of use cases, anonymous functions are often used as callback functions or event handlers, where the focus is on the functionality of the function rather than its identity. For example:

```js
setTimeout(function () {
  console.log("Hello, world!");
}, 5000);
```

In this example, an anonymous function is passed as a callback to the setTimeout() method, which will execute the function after a delay of 5 seconds. The function itself doesn't need a name, as it is only used once and its identity is not important.

Named functions, on the other hand, are typically used when the function is going to be reused or is part of an API. A named function can be called multiple times from different parts of the code, making it easier to maintain and debug. For example:

```js
function addNumbers(a, b) {
  return a + b;
}
```

In this example, a named function called "addNumbers" is defined that takes two parameters and returns their sum. This function can be called from anywhere in the code by name, making it more reusable and easier to maintain.

So, in summary, anonymous functions are useful for one-off tasks, such as callbacks or event handlers, where the function's identity is not important. Named functions, on the other hand, are useful for functions that will be reused or are part of an API, where their identity is important and they need to be called by name from different parts of the code.

## **32. What is function composition, and how can it be used in JavaScript?**

Function composition is a technique in functional programming where two or more functions are combined to create a new function. The output of one function becomes the input to the next function, and so on, until the final result is returned.

In JavaScript, function composition can be achieved using higher-order functions such as map, filter, and reduce. These functions take other functions as arguments, allowing you to chain them together to achieve complex operations on collections of data.

For example, let's say you have an array of numbers and you want to perform several operations on it - first, you want to filter out all the even numbers, then you want to double each remaining number, and finally, you want to sum up the resulting numbers. You could achieve this using function composition like this:

```js
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter((num) => num % 2 !== 0) // keep only odd numbers
  .map((num) => num * 2) // double each number
  .reduce((acc, num) => acc + num, 0); // sum up the results

console.log(result); // Output: 18
```

In this example, we first use the filter() method to keep only the odd numbers in the array, then we use the map() method to double each remaining number, and finally, we use the reduce() method to sum up the resulting numbers.

By combining these three methods using function composition, we were able to achieve our goal with concise and readable code.

Overall, function composition is a powerful technique in JavaScript that can help you create complex operations by chaining together simple functions. It allows you to write code that is both reusable and easy to read, making it a valuable tool for any JavaScript developer.

## **33. What is a closure factory, and how can it be used?**

In JavaScript, a closure is created when a function is defined inside another function and the inner function has access to the outer function's variables. A closure factory is a design pattern that uses closures to create a family of related functions.

A closure factory can be used to create multiple functions with similar functionality but different configurations. For example, let's say we have a function called `counter` that returns a new function each time it is called. Each returned function should count the number of times it has been called.

Here's an example implementation of a closure factory in JavaScript:

```js
function counter() {
  let count = 0;

  return function () {
    count++;
    console.log(`Count: ${count}`);
  };
}

const counter1 = counter();
counter1(); // Output: Count: 1
counter1(); // Output: Count: 2

const counter2 = counter();
counter2(); // Output: Count: 1
```

In this example, `counter()` is the closure factory. It creates a new closure every time it's called, and each closure has its own `count` variable. The returned function updates the `count` variable and logs the current count to the console.

By using a closure factory, we can create multiple counters with their own independent counts, without having to duplicate code or define separate variables for each count.

## **34. What is the difference between `slice()` and `splice()`?**

`slice()` and `splice()` are two different methods in JavaScript arrays that have different functionality.

- `slice()` method creates a new array from an existing array by copying a portion of the original array into the new array. It does not modify the original array. `slice()` takes two optional arguments, start and end, which define the slice of the array to be returned. The start argument specifies the index at which to begin the extraction (inclusive), and the end argument specifies the index at which to end the extraction (exclusive). If either argument is omitted, slice() will copy all elements from the start index to the end of the array.

Here's how `slice()` works behind the scenes:

1.  A new empty array is created.
2.  The start and end indexes are evaluated, and the resulting range of values is extracted from the original array and added to the new array.
3.  The new array is returned.

Here's an example:

```js
const arr = [1, 2, 3, 4, 5];
const slicedArr = arr.slice(1, 4);

console.log(slicedArr); // Output: [2, 3, 4]
console.log(arr); // Output: [1, 2, 3, 4, 5]
```

In this example, `slice()` returns a new array with values `[2, 3, 4]`, and the original array remains unchanged.

- `splice()` method modifies an existing array by adding or removing elements from it. It takes three arguments: start index, delete count, and any new elements to add. The start index determines where the changes should begin, the delete count specifies how many elements to remove from the array starting at the start index, and any additional arguments passed to splice() adds new elements to the array after the deleted elements.

Here's how `splice()` works behind the scenes:

1.  Elements are removed from the original array starting with the start index and continuing for the length of the delete count.
2.  Any new elements passed as arguments to `splice()` are inserted at the position of the start index.
3.  The modified original array is returned.

Here's an example:

```js
const arr = [1, 2, 3, 4, 5];
arr.splice(1, 2, "a", "b");

console.log(arr); // Output: [1, 'a', 'b', 4, 5]
```

In this example, `splice()` removes 2 elements starting at index 1 (`[2, 3]`) and replaces them with `'a'` and `'b'`, resulting in the modified array `[1, 'a', 'b', 4, 5]`.

## **35. What are the different types of scopes in JavaScript?**

In JavaScript, there are two main types of scopes:

1.  **Global Scope**: The global scope is the outermost scope and is accessible from any part of the code. Variables declared outside of any function or block belong to the global scope.

Here's an example:

```js
const globalVar = "This is a global variable";

function myFunction() {
  console.log(globalVar); // Output: This is a global variable
}

myFunction();
```

2.  **Local Scope or Function Scope**: A local scope, also known as a function scope, is created when a function is defined. Variables declared inside the function belong to the local scope and can only be accessed within that function.

Here's an example:

```js
function myFunction() {
  const localVar = "This is a local variable";
  console.log(localVar); // Output: This is a local variable
}

myFunction();
console.log(localVar); // Output: ReferenceError: localVar is not defined
```

In this example, `localVar` is declared inside the `myFunction()` function and belongs to the local scope. It can only be accessed within the function.

In addition to these two main types of scopes, there is also a concept of **block scope** introduced in ES6 with the introduction of let and const keywords. Variables declared using let and const are block-scoped, meaning they are only accessible within the block of code in which they are declared. A block is typically denoted by curly braces {} used in conjunction with control flow statements like if, for, while loops, etc.

Here's an example:

```js
if (true) {
  let blockVar = "This is a block variable";
  const anotherBlockVar = "This is another block variable";
}
console.log(blockVar); // Output: ReferenceError: blockVar is not defined
console.log(anotherBlockVar); // Output: ReferenceError: anotherBlockVar is not defined
```

In this example, `blockVar` and `anotherBlockVar` are declared inside an if block, and therefore belong to the block scope. They cannot be accessed outside of the block.

## **36. What is the difference between `split()` and `join()`?**

`split()` and `join()` are both methods available on JavaScript strings, but they have different functionality.

- `split()` method converts a string into an array by breaking the original string into substrings based on a specified separator. `split()` takes one argument, which is the separator to use for dividing the string. If no separator is provided, the entire string will be treated as a single element of the resulting array.

Here's an example:

```js
const str = "apple,banana,orange";
const arr = str.split(",");

console.log(arr); // Output: ['apple', 'banana', 'orange']
```

In this example, `split()` breaks the string at each comma `,` and returns an array with three elements: `'apple'`, `'banana'`, and `'orange'`.

- `join()` method converts an array into a string by concatenating all elements of the array together and separating them with a specified separator. `join()` takes one optional argument, which is the separator to use for joining the elements of the array. If no separator is provided, a comma will be used as the default separator.

Here's an example:

```js
const arr = ["apple", "banana", "orange"];
const str = arr.join("-");

console.log(str); // Output: 'apple-banana-orange'
```

In this example, `join()` concatenates all the elements of the array together, separated by a dash `-` and returns the resulting string `'apple-banana-orange'`.

In summary, `split()` splits a string into an array of substrings while `join()` joins an array of elements into a single string using a specified separator.

## **37. What is the difference between `event.preventDefault()` and `event.stopPropagation()`?**

`event.preventDefault()` and `event.stopPropagation()` are both methods available in JavaScript for working with events, but they have different functionalities.

- `event.preventDefault()` is a method that prevents the default action of an event from occurring. For example, if you have a link with an attached `click` event that takes the user to a new page, calling `event.preventDefault()` within the event handler will prevent the link from navigating to the new page.

Here's an example:

```js
const link = document.querySelector("a");

link.addEventListener("click", (event) => {
  event.preventDefault(); // Prevents the default action of the click event
});
```

In this example, clicking the link will not navigate the user to the new page because `event.preventDefault()` is called within the event handler.

- `event.stopPropagation()` is a method that stops the propagation of an event through the DOM tree. When an event occurs on a DOM element, it propagates through its parent elements up to the top-most element of the DOM tree. Calling `event.stopPropagation()` within an event handler prevents the event from bubbling up the DOM tree any further.

Here's an example:

```js
const parent = document.querySelector(".parent");
const child = document.querySelector(".child");

parent.addEventListener("click", () => {
  console.log("Clicked parent");
});

child.addEventListener("click", (event) => {
  console.log("Clicked child");
  event.stopPropagation(); // Stops the event from propagating to the parent
});
```

In this example, clicking the child element will log `'Clicked child'` to the console, but will not trigger the click event on the parent element because `event.stopPropagation()` is called within the child event handler.

In summary, `event.preventDefault()` prevents the default action of an event from occurring while `event.stopPropagation()` stops the event from propagating any further up the DOM tree.

## **38. What is the difference between `array.map()` and `array.forEach()`?**

`array.map()` and `array.forEach()` are both methods available in JavaScript for working with arrays, but they have different functionalities.

- `array.map()` method creates a new array with the results of calling a provided function on every element in the array. `map()` returns a new array containing the transformed elements, without modifying the original array. The provided function takes three arguments: the current value of the element being processed, the index of the current element, and the entire array.

Here's an example:

```js
const arr = [1, 2, 3, 4];
const newArr = arr.map((num) => {
  return num * 2;
});

console.log(newArr); // Output: [2, 4, 6, 8]
console.log(arr); // Output: [1, 2, 3, 4] (original array is not changed)
```

In this example, `map()` applies the function `(num) => { return num * 2; }` to each element of the original array and returns a new array with the transformed elements.

- `array.forEach()` method executes a provided function once for each array element. `forEach()` does not return anything and just operates on the original array. The provided function takes three arguments: the current value of the element being processed, the index of the current element, and the entire array.

Here's an example:

```js
const arr = [1, 2, 3, 4];
arr.forEach((num, index) => {
  console.log(`Element ${index}: ${num}`);
});

// Output:
// Element 0: 1
// Element 1: 2
// Element 2: 3
// Element 3: 4
```

In this example, `forEach()` applies the function `(num, index) => { console.log(`Element ${index}: ${num}`); }` to each element of the original array and logs the result to the console.

In summary, `array.map()` creates a new array by applying a transformation function to each element of the original array while `array.forEach()` iterates over the elements of the array and performs a specified action for each element, without returning a new array.

## **39. What is the difference between `encodeURIComponent()` and `encodeURI()`?**

`encodeURIComponent()` and `encodeURI()` are both methods available in JavaScript for encoding a URI, but they have different functionalities.

- `encodeURIComponent()` method encodes all characters in a URI component (part of the URI delimited by slashes, question marks, and hashes) by replacing each character with its UTF-8 percent-encoded equivalent. This method is typically used to encode data passed as part of the query string or fragment identifier.

Here's an example:

```js
const uriComponent = "https://example.com/search?q=JavaScript & CSS";

const encodedComponent = encodeURIComponent(uriComponent);

console.log(encodedComponent); // Output: 'https%3A%2F%2Fexample.com%2Fsearch%3Fq%3DJavaScript%20%26%20CSS'
```

In this example, `encodeURIComponent()` replaces all special characters in the `uriComponent` string with their UTF-8 percent-encoded equivalents.

- `encodeURI()` method encodes only certain characters in a URI by replacing each character that is not a letter, number, or one of the following characters: `; , / ? : @ & = + $ - _ . ! ~ * ' ( ) #`. This method is typically used to encode a complete URI.

Here's an example:

```js
const uri = "https://example.com/search?q=JavaScript & CSS";

const encodedUri = encodeURI(uri);

console.log(encodedUri); // Output: 'https://example.com/search?q=JavaScript%20&%20CSS'
```

In this example, `encodeURI()` replaces only the special characters in the `uri` string with their percent-encoded equivalents. Note that the ampersand `&` character is not encoded because it is a valid separator between query string parameters.

In summary, `encodeURIComponent()` encodes all characters in a URI component while `encodeURI()` encodes only certain characters in a complete URI.

## **40. What is the difference between local storage and session storage?**

`localStorage` and `sessionStorage` are both mechanisms available in modern web browsers that allow web applications to store data on the client-side. However, there are some key differences between them.

- **LocalStorage**: `localStorage` allows web applications to store key/value pairs locally within the browser with no expiration date until explicitly cleared by the user or the web application. This means that stored data is persistent and will remain available even after the browser window is closed or the computer is restarted. The data stored in `localStorage` is specific to the domain that created it, so it cannot be accessed by other domains.

Here's an example:

```js
// Set a value in localStorage
localStorage.setItem("myKey", "myValue");

// Get a value from localStorage
const myValue = localStorage.getItem("myKey");
console.log(myValue); // Output: 'myValue'
```

In this example, the `localStorage.setItem()` method sets a key/value pair in the `localStorage`, and `localStorage.getItem()` retrieves the value of the specified key.

- **SessionStorage**: `sessionStorage` allows web applications to store key/value pairs locally within the browser for the duration of a single session only. This means that stored data is not persistent and will be lost once the current browsing session ends (i.e., when the user closes the browser window or tab). The data stored in `sessionStorage` is specific to the domain that created it, so it cannot be accessed by other domains.

Here's an example:

```js
// Set a value in sessionStorage
sessionStorage.setItem("myKey", "myValue");

// Get a value from sessionStorage
const myValue = sessionStorage.getItem("myKey");
console.log(myValue); // Output: 'myValue'
```

In this example, the `sessionStorage.setItem()` method sets a key/value pair in the `sessionStorage`, and `sessionStorage.getItem()` retrieves the value of the specified key.

In summary, `localStorage` and `sessionStorage` both allow web applications to store data on the client-side, but `localStorage` stores data persistently with no expiration date until explicitly cleared, while `sessionStorage` stores data only for the duration of a single session until the user ends the browsing session. The data stored in both is specific to the domain that created it and cannot be accessed by other domains.

## **41. What is the difference between `Object.create()` and `new` keyword?**

`Object.create()` and the `new` keyword are both methods available in JavaScript for creating objects, but they have different functionalities.

- `Object.create()`: this method creates a new object with the specified prototype object and any additional properties provided as an argument. It allows you to create an object that inherits from another object, without having to define a constructor function. The prototype of the newly created object is set to the object passed as the first parameter to `Object.create()`, or to the `null` value if no argument is passed.

Here's an example:

```js
const person = {
  name: "John Doe",
  age: 30,
  greet: function () {
    console.log(`Hello, my name is ${this.name}`);
  },
};

const john = Object.create(person);

john.name = "John";
john.greet(); // Output: 'Hello, my name is John'
```

In this example, `Object.create()` creates a new object `john` that has the same properties and methods as the `person` object. `john` inherits the `name`, `age`, and `greet()` method from the `person` object. The `name` property of `john` is then set to `'John'`.

- `new` keyword: when used with a constructor function, the `new` keyword creates a new instance of the object defined by the constructor function. The `new` keyword creates a new empty object and sets its prototype to the `prototype` property of the constructor function. It then calls the constructor function with the newly created object as the `this` context and returns the newly created object.

Here's an example:

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function () {
  console.log(`Hello, my name is ${this.name}`);
};

const john = new Person("John", 30);

john.greet(); // Output: 'Hello, my name is John'
```

In this example, the `Person` constructor function defines a new `Person` object with `name` and `age` properties and a `greet()` method on its prototype. Using the `new` keyword with the `Person` constructor function creates a new instance of the `Person` object, sets its `name` and `age` properties to `'John'` and `30`, respectively, and returns the newly created object. The `greet()` method can be called on the newly created object `john`.

In summary, `Object.create()` creates a new object that inherits from an existing object, while the `new` keyword creates a new instance of an object defined by a constructor function.

## **42. Explain the difference between a static method and an instance method.**

In JavaScript, there are two types of methods available in object-oriented programming: static methods and instance methods. They have different functionality and usage.

- **Static methods** are methods that belong to the class itself, rather than to an instance of the class. Static methods are called on the class directly, rather than on an instance of the class. These methods can be used for utility or helper functions that do not require access to the state of individual instances of the class. Static methods are defined using the `static` keyword.

Here's an example:

```js
class Calculator {
  static add(x, y) {
    return x + y;
  }
}

const result = Calculator.add(2, 3);
console.log(result); // Output: 5
```

In this example, `add()` is a static method of the `Calculator` class. It takes two arguments and returns their sum. The `add()` method is called directly on the `Calculator` class, without creating an instance of the class.

- **Instance methods** are methods that belong to the individual instances of a class. Instance methods are defined inside the constructor function of the class or on the class's prototype object. These methods are called on instances of the class, and they have access to the state of the instance.

Here's an example:

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const john = new Person("John", 30);
john.greet(); // Output: 'Hello, my name is John'
```

In this example, `greet()` is an instance method of the `Person` class. It logs a greeting message with the name of the instance. The `greet()` method is called on the `john` instance of the `Person` class.

In summary, static methods belong to the class itself and are called on the class directly, while instance methods belong to individual instances of the class and are called on those instances. Static methods are useful for utility functions that don't require access to the state of individual instances, while instance methods are useful for working with the state of individual instances.

## **43. What is the difference between `array.reduce()` and `array.filter()`?**

`array.reduce()` and `array.filter()` are both methods available in JavaScript for working with arrays, but they have different functionalities.

- `array.reduce()` is a method that reduces an array of values to a single value by applying a specified function to each element of the array. The specified function takes two arguments: the accumulated value (initialized to the first element of the array or to a provided initial value) and the current value of the element being processed. The result of each function call is passed as the accumulated value to the next function call, and the final accumulated value is returned at the end.

Here's an example:

```js
const arr = [1, 2, 3, 4];
const sum = arr.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 10
```

In this example, `reduce()` applies the function `(accumulator, currentValue) => { return accumulator + currentValue; }` to each element of the original array and returns the sum of all elements.

- `array.filter()` is a method that creates a new array with all elements that pass a specified test. The specified test is defined in a function that takes one argument: the current value of the element being processed. If the function returns `true`, the element is included in the new array; if it returns `false`, the element is excluded.

Here's an example:

```js
const arr = [1, 2, 3, 4];
const evenNumbers = arr.filter((num) => {
  return num % 2 === 0;
});

console.log(evenNumbers); // Output: [2, 4]
```

In this example, `filter()` applies the function `(num) => { return num % 2 === 0; }` to each element of the original array and returns a new array containing only the even numbers.

In summary, `array.reduce()` reduces an array to a single value by applying a specified function to each element of the array, while `array.filter()` creates a new array with all elements that pass a specified test defined in a function.

## **44. What is the difference between `Array.from()` and `Array.of()`?**

`Array.from()` and `Array.of()` are both methods available in JavaScript for creating arrays, but they have different functionalities.

- `Array.from()` method creates a new array from an array-like or iterable object. The array-like or iterable object can be a string, an array-like object (such as the arguments object), or any iterable object (such as a Set, Map, or NodeList). It also allows you to apply a mapping function to each element of the original object. The mapped result is stored in the new array.

Here's an example:

```js
const str = "hello";
const arr = Array.from(str, (char) => {
  return char.toUpperCase();
});

console.log(arr); // Output: ['H', 'E', 'L', 'L', 'O']
```

In this example, `Array.from()` creates a new array by converting the `str` string into an array and applying the mapping function `(char) => { return char.toUpperCase(); }` to each element of the original string. The returned value is stored in the new array.

- `Array.of()` method creates a new array with the specified arguments as its elements. This method is useful when you want to create an array with a specified number of elements or when you want to create an array with a single element (which would be ambiguous using the array literal notation).

Here's an example:

```js
const arr1 = Array.of(1, 2, 3, 4);
console.log(arr1); // Output: [1, 2, 3, 4]

const arr2 = Array.of(5);
console.log(arr2); // Output: [5]
```

In this example, `Array.of()` creates a new array with the specified elements. In the first example, it creates an array with four elements; in the second example, it creates an array with a single element.

In summary, `Array.from()` creates a new array from an array-like or iterable object and allows you to apply a mapping function to each element of the original object, while `Array.of()` creates a new array with the specified arguments as its elements.

## **45. What is the difference between a truthy and falsy value in JavaScript?**

In JavaScript, a truthy value is a value that is considered "true" when evaluated in a Boolean context, whereas a falsy value is a value that is considered "false" when evaluated in a Boolean context.

The following values are considered falsy in JavaScript:

- `false`
- `null`
- `undefined`
- `0` (numeric zero)
- `-0` (negative zero)
- `NaN` (Not-a-Number)
- `''` (empty string)

All other values are considered truthy, including:

- All non-empty strings (including whitespace characters like spaces and tabs)
- All numbers, except for `0`, `-0`, and `NaN`
- All objects, including arrays and functions
- The special keyword `true`

Here's an example:

```js
if ("hello") {
  console.log("Truthy");
} else {
  console.log("Falsy");
}
// Output: 'Truthy'

if (0) {
  console.log("Truthy");
} else {
  console.log("Falsy");
}
// Output: 'Falsy'
```

In this example, the string `'hello'` is a truthy value and will result in the output `'Truthy'`. The number `0` is a falsy value and will result in the output `'Falsy'`.

Truthy and falsy values are often used in conditional statements such as `if` statements or ternary operators to determine whether a variable or expression has a value or not. For example:

```js
const name = "";

if (name) {
  console.log(`Hello, ${name}`);
} else {
  console.log("Name is not defined");
}
// Output: 'Name is not defined'
```

In this example, the `name` variable contains an empty string (`''`), which is a falsy value. Therefore, the `else` block is executed instead of the `if` block.

In summary, truthy values are those that evaluate to `true` in a Boolean context, while falsy values are those that evaluate to `false`. Knowing which values are truthy and falsy can be useful for writing more efficient and concise code that checks for the presence of values or conditions.

## **46. What is the difference between `Math.floor()` and `Math.round()`?**

`Math.floor()` and `Math.round()` are both methods available in JavaScript for working with number values, but they have different functionalities.

- `Math.floor()` method returns the largest integer less than or equal to a given number. It rounds down the number to its nearest integer value.

Here's an example:

```js
console.log(Math.floor(3.7)); // Output: 3
console.log(Math.floor(-3.7)); // Output: -4
```

In this example, `Math.floor()` rounds the number `3.7` down to `3`, and `-3.7` down to `-4`.

- `Math.round()` method returns the value of a given number rounded to the nearest integer. If the fractional part of the number is less than 0.5, the number is rounded down; if it is greater than or equal to 0.5, the number is rounded up.

Here's an example:

```js
console.log(Math.round(3.2)); // Output: 3
console.log(Math.round(3.7)); // Output: 4
console.log(Math.round(-3.2)); // Output: -3
console.log(Math.round(-3.7)); // Output: -4
```

In this example, `Math.round()` rounds the number `3.2` down to `3`, `3.7` up to `4`, `-3.2` up to `-3`, and `-3.7` down to `-4`.

In summary, `Math.floor()` rounds a number down to its nearest integer value, while `Math.round()` rounds a number to the nearest integer (with rounding up or down depending on whether the fractional part is less than or greater than or equal to 0.5).

## **47. What is the difference between a stack and a queue?**

In JavaScript, a stack and a queue are both abstract data types, which are used to store and manipulate collections of data. They have different behaviors and usage.

- A **stack** is a linear data structure that follows the Last-In-First-Out (LIFO) principle. In a stack, the last element added to the collection is the first one to be removed. This behavior makes stacks useful for implementing undo/redo functionality, maintaining call stacks in recursive functions, and parsing expressions.

Here's an example of using a stack to reverse a string:

```js
function reverseString(str) {
  const stack = [];

  for (let i = 0; i < str.length; i++) {
    stack.push(str[i]);
  }

  let reversedStr = "";

  while (stack.length > 0) {
    reversedStr += stack.pop();
  }

  return reversedStr;
}

console.log(reverseString("hello")); // Output: 'olleh'
```

In this example, `reverseString()` function uses a stack to push each character of the input string onto the stack. The function then pops each character off the stack and concatenates it to a new string in reverse order.

- A **queue** is a linear data structure that follows the First-In-First-Out (FIFO) principle. In a queue, the first element added to the collection is the first one to be removed. This behavior makes queues useful for implementing job scheduling, message passing, and asynchronous programming.

Here's an example of using a queue to process messages:

```js
const messageQueue = [];

function sendMessage(message) {
  messageQueue.push(message);
}

function processMessages() {
  while (messageQueue.length > 0) {
    const message = messageQueue.shift();
    console.log(`Processing message: ${message}`);
  }
}

sendMessage("Hello");
sendMessage("World");
processMessages();
// Output:
// Processing message: Hello
// Processing message: World
```

In this example, `sendMessage()` function adds a message to the end of the message queue using the `push()` method. The `processMessages()` function processes each message in the queue by removing the first message using the `shift()` method and logging it to the console.

In summary, a stack follows the LIFO principle, while a queue follows the FIFO principle. Stacks are useful for reversing and parsing operations, while queues are useful for managing job scheduling and message processing.

## **48. What is the difference between `querySelector()` and `getElementById()`?**

`querySelector()` and `getElementById()` are both methods available in JavaScript for selecting elements from the DOM, but they have some differences in their functionality and usage.

- `querySelector()` is a method that allows you to select an element from the DOM using a CSS selector. It returns the first matching element, or null if no matches are found.

Here's an example:

```js
const element = document.querySelector(".my-class");
```

In this example, `querySelector()` selects an element with the class name 'my-class'. The returned value is the first element that matches the selector.

`querySelector()` can be useful when you want to select an element by a specific attribute, such as class or data attribute, or when you want to use more complex selectors like :hover and :nth-child(n).

- `getElementById()` is a method that allows you to select an element from the DOM using its unique ID. It returns the element with the matching ID, or null if no match is found.

Here's an example:

```js
const element = document.getElementById("my-id");
```

In this example, `getElementById()` selects an element with the ID 'my-id'. The returned value is the element that matches the ID.

`getElementById()` is useful when you want to select an element with a known ID, which is unique within the document.

In terms of performance, `getElementById()` is generally faster than `querySelector()`, because it only searches for elements by ID, which is the fastest way to locate an element in the DOM. However, `querySelector()` is more flexible and allows you to select elements using more complex selectors.

In summary, `querySelector()` is used to select elements from the DOM using CSS selectors, while `getElementById()` is used to select elements from the DOM using their unique ID. Both methods have their own use cases, and choosing between them depends on the specific needs of your application.

## **49. What is the difference between `local` and `global` variables in JavaScript?**

In JavaScript, variables can be declared with either a `var`, `let`, or `const` keyword. Variables declared using `var` are function-scoped, while variables declared with `let` and `const` are block-scoped. This means that the scope of a variable determines its accessibility and lifetime. Based on scope, there are two types of variables in JavaScript: local and global.

- **Local Variables**: Variables declared inside a function block using the `var`, `let`, or `const` keyword are considered local to that function. Local variables have functional scope, which means they are only accessible from within the function where they are declared. They are created when the function is called and destroyed when the function returns.

Here's an example:

```js
function myFunction() {
  var x = 5; // local variable
  console.log(x); // Output: 5
}

myFunction();

console.log(x); // Output: ReferenceError: x is not defined
```

In this example, the variable `x` is declared inside the `myFunction()` function block and is therefore a local variable. It is only accessible from within the function, and trying to access it outside the function will result in a `ReferenceError`.

- **Global Variables**: Variables declared outside any function block or without any keywords (`var`, `let`, `const`) are considered global variables. Global variables have global scope, which means they can be accessed from anywhere in the code, including inside functions. They are created when the script is loaded and destroyed when the browser window is closed or the page is refreshed.

Here's an example:

```js
var y = 10; // global variable

function myFunction() {
  console.log(y); // Output: 10
}

myFunction();

console.log(y); // Output: 10
```

In this example, the variable `y` is declared outside the `myFunction()` function block and is therefore a global variable. It can be accessed from within the function and outside of it.

It is generally recommended to minimize the use of global variables as much as possible, because they can cause naming conflicts and make code harder to maintain and debug. Instead, try to use local variables to encapsulate data and avoid unintended side effects.

In summary, local variables have functional scope and are only accessible from within the function where they are declared, while global variables have global scope and can be accessed from anywhere in the code.

## **50. What is the difference between `Object.freeze()` and `Object.seal()`?**

`Object.freeze()` and `Object.seal()` are both methods available in JavaScript for controlling the mutability of objects, but they have different functionalities and levels of restriction.

- `Object.freeze()` method freezes an object, making it immutable. Once an object is frozen, its properties cannot be added, removed, or modified. Any attempt to modify a frozen object will result in a `TypeError`.

Here's an example:

```js
const obj = {
  x: 1,
  y: 2,
};

Object.freeze(obj);

obj.z = 3; // This has no effect

console.log(obj); // Output: { x: 1, y: 2 }

obj.x = 4; // This throws a TypeError
```

In this example, `Object.freeze()` makes the `obj` object immutable, which means that you cannot add new properties to it or modify its existing properties. The attempted modification of the `z` property has no effect, and the attempted modification of the `x` property throws a `TypeError`.

- `Object.seal()` method seals an object, preventing new properties from being added and marking all existing properties as non-configurable. This means that the properties can still be modified, but they cannot be deleted or reconfigured using methods like `Object.defineProperty()`.

Here's an example:

```js
const obj = {
  x: 1,
  y: 2,
};

Object.seal(obj);

obj.z = 3; // This has no effect

console.log(obj); // Output: { x: 1, y: 2 }

delete obj.x; // This has no effect

console.log(obj); // Output: { x: 1, y: 2 }

Object.defineProperty(obj, "x", { writable: false }); // This throws a TypeError
```

In this example, `Object.seal()` makes the `obj` object sealed, which means that you cannot add new properties to it or delete its existing properties. The attempted modification of the `z` property has no effect, and the attempted deletion of the `x` property also has no effect. However, the `x` property can still be modified because it is writable by default. The attempted configuration of the `x` property using `Object.defineProperty()` throws a `TypeError` because it is not configurable.

In summary, `Object.freeze()` makes an object completely immutable, while `Object.seal()` only prevents new properties from being added and marks all existing properties as non-configurable to prevent them from being deleted or reconfigured. Use `Object.freeze()` when you need full immutability, and use `Object.seal()` when you want to restrict certain operations on an object while still allowing its properties to be modified.
