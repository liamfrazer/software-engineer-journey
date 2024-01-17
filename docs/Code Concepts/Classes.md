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
        console.log(`Product: ${this.name}`); // Product: Shirt
        console.log(`Price: $${this.price}`); // Price: $19.99
    }
}

const product1 = new Product("Shirt", 19.99);

product1.displayProduct();
```

