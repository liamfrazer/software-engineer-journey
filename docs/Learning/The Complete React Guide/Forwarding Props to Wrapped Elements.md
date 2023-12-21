---
tags:
  - react
  - props
  - forwarding
  - wrapped
  - elements
  - rest
---
# Forwarding Props to Wrapped Elements
* This JavaScript feature is called "Rest property"
* This syntax groups all remaining object properties into a new object (named "props" in this case)

```jsx
export default function Section({ title, children, ...props }) {
	return (
		<section {...props}>
			<h2>{title}</h2>
			{children}
		</section>
	);
}
```

* All the props that were not manually extracted like `title` or `children` in our example, will all be merged into the `props` element with `...props` and then spread out again in `<section {...props}`
* This can be a very useful pattern when building wrapper components
* We now have a very flexible wrapper component

* We merge any leftover props into the `props` object with `...props`
* Then we can spread the remaining props with `button {...props}` onto the built in button
* We just have to ensure,