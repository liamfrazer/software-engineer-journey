---
tags:
  - react
  - CSS
  - inline
  - styles
---
# Styling React apps with Inline Styles
* Styles are applied within the JSX code instead of separate CSS files

* The style prop takes a dynamic value `{}` and then you pass an object as a value to the style prop
```jsx
			<p style={{ color: "red" }}>A community of artists and art-lovers.</p>

```

## Advantages
* Quick and easy to add to JSX
* Styles only affect the element to which you add them

## Disadvantages
* You need to know CSS
* You need to style every element individually
* There is no separation between JSX and CSS
