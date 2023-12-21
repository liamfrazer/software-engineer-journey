---
tags:
  - react
  - props
  - forwarded
  - elements
---
# Props are not Forwarded to Inner Elements

```jsx
export default function Section({ title, children }) {
	return (
		<section>
			<h2>{title}</h2>
		</section>
	);
}
```

* Expecting a title prop to be passed through, using props destructuring
* Using the special children prop, so that we can use the section as a wrapper around the actual section content.
* 