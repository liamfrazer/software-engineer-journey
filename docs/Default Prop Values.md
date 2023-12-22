---
tags:
  - default
  - props
  - values
  - react
  - components
---
# Default Prop Values

```jsx
const Tabs = ({ children, buttons, buttonsContainer = "menu" }) => {
	const ButtonsContainer = buttonsContainer;
	return (
		<>
			<ButtonsContainer>{buttons}</ButtonsContainer>
			{children}
		</>
	);
};

export default Tabs;
```

* By setting defaults, this means that the `"menu"` would still be recognised correctly, meaning the menu elements would still be functionality

