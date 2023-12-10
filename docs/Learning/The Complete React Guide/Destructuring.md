---
tags:
  - destructure
  - destructuring
  - arrays
  - objects
  - function-parameter
---
# Destructuring

* On the right side, they will create a new array
* On the left side, they will destructure the array
```js
const [] = ["Liam", "Frazer"];
```

* The [] syntax can be used to pull values out of an array.

```js
const [firstName, lastName] = ["Liam", "Frazer"];
console.log(firstName, lastName)
```

* The destructuring syntax also exists for objects, it doesn't just exist for arrays.

```js
const { name, age } = { name: "Liam", age: 25 };
console.log(name, age); // Liam 25
```
* On the right side, this will create an object
* On the left side, this will destructure an object.
* We have to use the field names that are defined in the object, whereas arrays are pulled out by position.

* An alias can also be defined when destructuring the object

```js
const { name: userName, age } = { name: "Liam", age: 25 };
console.log(userName, age); // Liam 25
```

* The destructuring syntax can also be used in `function parameter lists`
```js
function storeOrder({ id, currency }) {
  localStorage.setItem('id', id);
  localStorage.setItem('currency', currency);
}

console.log(storeOrder(({ id: 1, currency: "USD" })))
console.log(localStorage)
```

* Instead of accessing the order properties via the `dot notation` inside the storeOrder function body, you could use the destructuring code above.
* Instead `id` and `currency` are pulled out of the incoming object.
* storeOrder still only takes one parameter, it does not accept two parameters. Instead, it's one single parameter, an object which then just is destructured internally.



