---
tags:
  - react
  - portals
---
# Detaching DOM Rendering from JSX Structure with Portals
* Technically, it would make more sense for the overlay element to be output directly within a body or a `div`
* A deeply nested element could be hidden by other elements

```jsx
import { createPortal } from "react-dom";
```
* The idea is to teleport the HTML code into a different place within the DOM
* This wraps the returned JSX and then a second value is passed from the main HTML file



