---
tags:
  - react
  - CSS
  - conditional
  - classes
  - ternarny
---
# Dynamic and Conditional Styling with CSS files and CSS Classes

```jsx
className={emailNotValid ? "invalid" : undefined}
```

* Ternary should be used if the conditional class is not being applied
* Using `false` as a className wouldn't work correctly

* Backticks/template literals can be used to dynamically set multiple styling conditions
* Hard coded classNames can be applied with dynamically injected values that are based upon conditions

```jsx
<label className={`label ${emailNotValid ? "invalid" : ""}`}>
	Email
</label>
```

