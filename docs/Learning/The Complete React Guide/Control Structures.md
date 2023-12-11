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
* For loops are required to execute the same amount of code multiple times

```js
const hobbies = ["Fishing", "Sports", "Cooking"];
for (const hobby of hobbies) {};
// Fishing
// Sports
// Cooking
```
* We're telling JavaScript to make a new const for every item within the array, then execute the code within the curly braces to go through all the elements as often as required.
* For our `hobbies` array, this will go through the functionality 3 times