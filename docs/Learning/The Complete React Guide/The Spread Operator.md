---
tags:
  - spread
  - operator
  - array
  - objects
---
# The Spread Operator
* The spread operator pulls out values from an array, then adds them as separated comma values to a new array.
* The spread operator functions on both arrays and objects

```js
const hobbies = ["Fishing", "Sports", "Cooking"];
const newHobbies = ["Hiking"];
const mergedHobbies = [...newHobbies, ...hobbies];

console.log(mergedHobbies) // ["Hiking", "Fishing"]
```

```js
const user = {
  name: "Liam",
  age: 25
};

const extendedUser = {
  isAdmin: true,
  ...user
}

console.log(extendedUser) // Object { isAdmin: true, name: "Liam", age: 25 }
```


