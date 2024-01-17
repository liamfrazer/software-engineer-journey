---
tags:
  - classes
  - javascript
---
# Classes

## JavaScript

* Classes are am ES6 feature that provide a more structured and cleaner way to work with object.
* Cleaner than traditional constructor functions
* Helpful for static keyword, encapsulation, inheritance

```jsx
class Product {
    constructor(name, price) {
        this.name = name;
        this.price = price;
    }

    displayProduct() {
        console.log(`Product: ${this.name}`);
        console.log(`Price: $${this.price.toFixed(2)}`);
    }

    calculateTotal(salesTax) {
        return this.price + (this.price * salesTax);
    }
}

const salesTax = 0.05;

const product1 = new Product("Shirt", 19.99);
const product2 = new Product("Pants", 22.50);
const product3 = new Product("Boxers", 24.99);


product1.displayProduct();
product2.displayProduct();
product3.displayProduct();

const total = product1.calculateTotal(salesTax);
console.log(`Total Price: (with ${salesTax * 100}% Tax): $${total.toFixed(2)}`);


//Product: Shirt, {}

```

