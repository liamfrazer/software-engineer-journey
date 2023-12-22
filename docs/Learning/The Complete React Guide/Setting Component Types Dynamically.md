---
tags:
  - react
  - jsx
  - components
  - dynamic
---
# Setting Component Types Dynamically

* For the Tabs component, we might want to use different wrapper elements in different points within the application

```jsx
export default function Tabs({ children, buttons }) {
	return (
		<>
			<menu>{buttons}</menu>
			{children}
		</>
	);
}

```

* We could use the identifier of a component as a value and pass this through as a prop, giving the developer more options/functionality to use the component in different ways
* Custom components must be passed as a dynamic value `{Component}`

* Setting `<buttonsContainer/>` instead of the menu would not work as it's not an uppercase character and it's trying to use a component that does not exist
* Instead, we would manually create one ourselves above

```jsx
export default function Tabs({ children, buttons, buttonsContainer }) {
	const ButtonsContainer = buttonsContainer;
	return (
		<>
			<ButtonsContainer>{buttons}</ButtonsContainer>
			{children}
		</>
	);
}
```

* React will use the value from `buttonsContainter`, React recognises that we're either using a custom component or built in component such as `menu`

* We're now able to dynamically set the wrapper, but knowing about this pattern, passing a component identifier as a value for a prop, dynamically rendering different HTML elements

```jsx
const Tabs = ({ children, buttons, buttonsContainer }) => {
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

