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


