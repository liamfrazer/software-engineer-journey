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

```jsx
import classes from './Header.module.css'
```
```jsx
<p className={classes.paragraph}></p>
```

