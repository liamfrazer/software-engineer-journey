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
* 
