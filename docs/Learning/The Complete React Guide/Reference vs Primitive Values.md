---
tags:
  - Reference
  - Primitive
  - values
  - objects
  - arrays
  - const
---
# Reference vs Primitive Values

* Primitive values like strings cannot be edited.
* Even executing a method on the value with produce a new string instead of editing the old string.

* When dealing with objects & arrays, this is different
* An example when using array.push, push is editing the original array,  it mutated the original array
* Objects in JavaScript are reference values

* In a variable, you don't store the value but the address of data in memory is stored.
* When calling push, JavaScript will reach out to the address, then add the new item to the existing array in memory.

* This also is the reason why we can use `const` on an array, meaning the value can't be edited.
* Objects can be stored in a constant,