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

```jsx
		<Section title="Examples" id="examples">
			<menu>
				<TabButton
					isSelected={selectedTopic === "components"}
					onSelect={() => handleSelect("components")}
				>
					Components
				</TabButton>
				<TabButton
					isSelected={selectedTopic === "jsx"}
					onSelect={() => handleSelect("jsx")}
				>
					JSX
				</TabButton>
				<TabButton
					isSelected={selectedTopic === "props"}
					onSelect={() => handleSelect("props")}
				>
					Props
				</TabButton>
				<TabButton
					isSelected={selectedTopic === "state"}
					onSelect={() => handleSelect("state")}
				>
					State
				</TabButton>
			</menu>
			{tabContent}
		</Section>
```

* When setting props, on custom components those props are not automatically forwarded on the JSX code used within that component

![[Pasted image 20231221153513.png]]
* Props must be used & set explicitly
* In our example above, while the custom component has `id=examples` set, this isn't being used within the component we're displaying

```jsx
export default function Section({ title, children, id }) {
	return (
		<section id={id}>
			<h2>{title}</h2>
			{children}
		</section>
	);
}
```
![[Pasted image 20231221153741.png]]




