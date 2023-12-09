---
tags:
  - javascript
  - function
  - parameters
  - return
  - values
---
# functions and parameters

* Functions are used when you're defining code, that isn't executed immediately, but at some point when the function is called. A function can be called multiple times
* A function needs to be invoked to work

```js
function greet() {
  console.log('Hello World!');
}

greet() // Hello World!
```

* Functions can take parameters, knows as input values
* Parameters are then available within the scope of the function
* The idea behind parameters, is that you can have one re-usable function, that can be re-used with different input values
```js
function greet(userName, message) {
  console.log(`${message} ${userName}`);
}

greet("Liam", "Hello");
greet("Frazer", "Hello")
```

* You can assign default values to parameters, by adding a `=` sign
* The default value can be overridden, by simply providing a value
```js
function greet(userName, message = "Hello") {
  console.log(`${message} ${userName}`);
}

greet("Liam", "Hi"); // Hi Liam
greet("Frazer") // Hello Frazer
```

* Functions can also return values, by using the `return` keyword
* Functions must only have one return statement at most.
* Functions without `return` implicitly return `undefined`

* Whenever you create functions, you should describe what's inside of it, or what it does
* Functions can also be used for producing and returning values
* They should be named to ensure it's very clear what a function does

```js
function combine(a, b, c) {
  return a * b / c
}

console.log(combine(2, 3, 4)) // 1.5
```

## Arrow Functions
* Arrow functions are very popular with anonymous functions, where the function does not need a name
* 
