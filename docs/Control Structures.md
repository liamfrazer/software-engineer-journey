---
tags:
  - control
  - structures
  - for
  - loop
  - if
---
# Control Structures

* If statements are typically used to check content that you don't know in advanced

```js
const password = prompt('Your password: ');

if (password === "Hello") {
  console.log("Hello works");
} else if (password === "hello") {
  console.log("hello works");
} else {
  console.log("Wrong password/Access Denied");
}
```

* An important for loop that we use in JavaScript is the for loop while looping through an array