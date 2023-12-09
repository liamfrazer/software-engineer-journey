---
tags:
  - javascript
  - function
  - parameters
  - return
  - values
  - arrow
  - parentheses
  - statement
  - objects
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
* When using arrow functions, you cannot use the function keyword and instead use the parameter list, an arrow and then the curly braces
* The return keyword can still be used

### Omitting parameter list parentheses
* If your arrow functions take exactly one parameter, you may omit the wrapping parentheses
```js
userName => { ... }
(userName) => { ... }
```
* If the function takes no parameters, parentheses must not be omitted.
* If the function takes more than one parameter, you must also not omit parentheses

### Omitting function body curly braces
* If your arrow function contains no other logic, but a `return` statement, you may omit the curly braces and the `return` keyword
```js
number => {
	return number * 3;
}

number => number * 3;
```

### Special case: Just returning an object
* If you use the shorter alternative ` number => number * 3`  and you're attempting to return a JavaScript object, you may end up with invalid code.
* JavaScript treats the curly braces as `function body wrappers`
* To tell JavaScript that an object should be created (and returned) instead, the code would need to be adjusted
```js
number => ({ age: number}) // wrapping the object in extra parentheses
```
* By wrapping the object and its curly braces with an extra pair of parentheses, JavaScript understands that the curly braces are not there to define a `function body` but instead to create an object, now an object then gets returned.

