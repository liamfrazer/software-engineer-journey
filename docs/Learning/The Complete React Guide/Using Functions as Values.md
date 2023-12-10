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

