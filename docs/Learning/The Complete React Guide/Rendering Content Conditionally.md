---
tags:
  - rendering
  - conditional
  - components
  - react
  - ternery
---
# Rendering Content Conditionally
* We need to output content conditionally, in our example if a topic has been selected

* In the following code, we're saying that if we don't have a selected topic, render the paragraph, otherwise render nothing.

```jsx
	const [selectedTopic, setSelectedTopic] = useState();
```

```jsx
					{!selectedTopic ? (
						<p> Please select a topic.</p>
					) : (
						<div id="tab-content">
							<h3>{EXAMPLES[selectedTopic].title}</h3>
							<p>{EXAMPLES[selectedTopic].description}</p>
							<pre>
								<code>{EXAMPLES[selectedTopic].code}</code>
							</pre>
						</div>
					)}
```


