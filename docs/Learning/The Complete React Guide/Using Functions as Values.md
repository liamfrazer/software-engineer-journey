---
tags:
  - functions
  - values
  - anonymous
  - arrow
  - function
---
# Using Functions as Value

* Functions can be passed as values to other functions.
* We're creating an anonymous function
* When you're passing a function to another function

* By added parentheses to the function being passed through the first function, you would make sure that the function gets executed immediately, once the first function is set which then makes it the return value, if it would return any value
* In our example,  we don't want to pass the return value, but the function itself.
* Parenthesis must be omitted, so that the function is being passed as a value

```js
const handleTimeout = () => {
  console.log("Timeout");
}

setTimeout(handleTimeout(), 5000) // 5 second delay to console log
```

* An anonymous function can also be passed in advance, and then any code could then be executed within that anonymous arrow function
* When defining an anonymous function, you're also not executing that function, you're just defining it, then passing the defined function to the first function

```js
function greeter(greetFn) {
  greetFn();
}

greeter(() => console.log("Hello"))
```
* This function is getting executed, as we're passing it as a parameter for the greeter function.
* Inside the greet function, we're then executing the greetFn function.
* Passing functions as values is not limited to built in functions, but can be done with all functions.


* Here's a comparison:

|Aspect|Function Expression|Function Declaration|
|---|---|---|
|Syntax|Assigned to a variable|Standalone statement|
|Hoisting|Not hoisted|Hoisted to the top of scope|
|Named or Anonymous|Can be named or anonymous|Must have a name|
|Usage|Often used as a variable value|Used as standalone function|

* Both function expressions and function declarations have their use cases. Function expressions offer more flexibility and can be more versatile in certain scenarios, especially when creating functions dynamically or as values assigned to variables. Function declarations, on the other hand, are standalone and provide a cleaner syntax for defining functions directly.