---
tags:
  - react
  - CSS
  - scope
  - modules
  - rules
---
# Scoping CSS Rules with CSS Modules

* Adding .module. to the filename will change how the .css file is built
* This also means that we will be importing the file differently
* The className could also be applied conditionally similar to what we've seen previous with vanilla or inline CSS

```jsx
import classes from './Header.module.css'
```
```jsx
<p className={classes.paragraph}></p>
```

## Advantages
* CSS code is decoupled from JSC code
* You write CSS code
* CSS code can be written by another developer
* CSS classes are scoped to the component files which import them

## Disadvantages
* You need to know CSS
* You may end up with many relatively small CSS files in your project

