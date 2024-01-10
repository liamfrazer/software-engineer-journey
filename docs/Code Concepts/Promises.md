---
tags:
  - Promises
  - javascript
---
# Promises

## JavaScript

* https://www.youtube.com/watch?v=lfmg-EJ8gm4&t=38390s
* A `Promise` is an object that manages asynchronous operations.
* You wrap a `Promise` object around asynchronous code
* "I promise to return a value"
* PENDING > RESOLVED or REJECTED

```jsx
new Promise((resolved, reject) => {asyncronous code})
```

```jsx
// Do these chores in Order

// 1. Walk the dog
// 2. Clean the Kitchen
// 3. Take out the trash

function walkDog() {

    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const dogWalked = true;
            if (dogWalked) {
                resolve("You walked the dog.");
            } else {
                reject("You didn't walk the dog.")
            }
        }, 1500);
    });
}

function cleanKitchen() {

    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const kitchenCleaned = false;
            if (kitchenCleaned) {
                resolve("You cleaned the kitchen.");
            } else {
                reject("You didn't clean the kitchen.")
            }
        }, 2500);
    });
}

function takeOutTrash() {

    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const trashTakenOut = true;
            if (trashTakenOut) {
                resolve("You took out the trash.");
            } else {
                reject("You didn't take out the trash.")
            }
        }, 3500);
    })
}

walkDog().then(value => { console.log(value); return cleanKitchen() }) // You walked the dog.
    .then(value => { console.log(value); return takeOutTrash() })
    .then(value => { console.log(value); console.log('Done!') })
    .catch(error => { console.log(error) }); // You didn't clean the kitchen.
```

