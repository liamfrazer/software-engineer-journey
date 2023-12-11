---
tags:
  - functions
  - define
---
# Defining Functions Inside of Functions
* Functions defined within functions cannot be executed outside of that function
* In our example, `greet()` is defined within `init()` and therefore it's scoped to the function.
```js
function init() {
  function greet() {
    console.log("Hello");
  }

  greet();
}

init();
```

