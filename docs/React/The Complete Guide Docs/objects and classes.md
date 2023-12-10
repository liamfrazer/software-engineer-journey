---
tags:
  - objects
  - classes
  - methods
  - this
---
# objects and classes


```js
const user = {
  name: "Liam",
  age: 25,
}
console.log(user) // 
```


* Objects can store functions, that are then typically called `methods`
* If you are within a method, you can access the properties of the object, using the `this` keyword

* With the class keyword, you can create a "blueprint", that later could be used
* Class names should start with a capital and then methods can be included in
* The `contructor` function can be used to input parameters, then store them in properties of the object