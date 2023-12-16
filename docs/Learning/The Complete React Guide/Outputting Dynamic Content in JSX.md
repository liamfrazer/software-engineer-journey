---
tags:
  - react
  - dynamic
  - jsx
  - javascript
  - expression
  - statements
---
# Outputting Dynamic Content in JSX
* Static Content
	* Content that's hardcoded into the JSX code
	* Can't change at runtime
* Dynamic Content
	* Logic that produces the actual value is added to JSX
	* Content/value is derived at runtime

* Any JavaScript expression can be added into the JSX code
* if-statements, for-loops, function definitions and other block statements are not allowed here
* Only expression that directly produce a value

* Expressions produce a value
* Function statements do not produce a value

* Keeping your JSX code lean is preferred, where you would keep function expressions out of JSX, but only refer to them as their const 


```jsx
	const description = getRandomValue(values);

	return (
		<header>
			<img src="src/assets/react-core-concepts.png" alt="Stylized atom" />
			<h1>React Essentials</h1>
			<p>
				{description} React concepts you will need for almost any app
				you are going to build!
			</p>
		</header>
	);
}
```

