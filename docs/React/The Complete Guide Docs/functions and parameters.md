---
tags:
  - javascript
  - function
  - parameters
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
