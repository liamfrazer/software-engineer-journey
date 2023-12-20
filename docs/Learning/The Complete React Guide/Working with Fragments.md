---
tags:
  - jsx
  - react
  - fragments
---
# Working with Fragments
* JSX must have one parent element, commonly providing sibling elements within a parent div
* In JavaScript, we can only return one value with code, returning 2 siblings will not work for similar reasons.
* This means we will end up with an extra `<div>` and this is unnecessary
* We can use the fragment component instead `<>`


```jsx
return (
		<>
			<Header />
			<main>
```

