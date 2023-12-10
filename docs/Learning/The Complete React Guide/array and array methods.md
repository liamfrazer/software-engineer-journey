---
tags:
  - array
  - map
  - index
  - objects
  - push
---
# array and array methods
* The main idea behind an array is that you can create a list of values.
* Objects allow you to group values together with key value pairs, the main point of an array is to just have values stored in a certain order, accessed by their position.
* Using the index of the element, index always starts at 0
* Arrays are often used to store a list of values
* Arrays can contain any kind of values

* `array.push()` can be used to add another item to the array
* `array.findIndex()` allows you to find the index of a certain value, this will take a function as an input, this should accept at least one input parameter
```js
const hobbies = ["Fishing", "Sports", "Cooking"];

const index = hobbies.findIndex((hobby) => {
  return hobby === "Sports"
}); // 1
```

* The above arrow function can be shortened down even further

```js
const index = hobbies.findIndex((hobby) => hobby === "Sports");
```
* This is the shortest possible way of writing the arrow function
* We're defining a function, that takes an input called 
