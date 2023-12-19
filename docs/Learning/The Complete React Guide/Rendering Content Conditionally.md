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

* The `&&` value will output the condition that comes after it, if the condition in front of it is true.

```jsx
					{!selectedTopic && <p>Please select a topic.</p>}
					{selectedTopic && (
						<div id="tab-content">
							<h3>{EXAMPLES[selectedTopic].title}</h3>
							<p>{EXAMPLES[selectedTopic].description}</p>
							<pre>
								<code>{EXAMPLES[selectedTopic].code}</code>
							</pre>
						</div>
					)}
```

* JSX code can be stored in variables and constants

```jsx
	let tabContent = <p>Please select a topic.</p>;

	if (selectedTopic) {
		tabContent = (
			<div id="tab-content">
				<h3>{EXAMPLES[selectedTopic].title}</h3>
				<p>{EXAMPLES[selectedTopic].description}</p>
				<pre>
					<code>{EXAMPLES[selectedTopic].code}</code>
				</pre>
			</div>
		);
	}
```

```jsx
					{tabContent}
```



```jsx
import React from 'react';

export default function App() {
    
    const [alert, setAlert] = React.useState();
    
    const handleClick = () => {
        setAlert(!alert);
    }
    
    let warning = <button onClick={handleClick}>Delete</button>;
    
    if (alert) {
        warning = (
            <div data-testid="alert" id="alert">
            <h2>Are you sure?</h2>
            <p>These changes can't be reverted!</p>
            <button onClick={handleClick}>Proceed</button>
        </div>
        );
    };
    
    return (
      <div>
        {warning}
      </div>    
    );
}
```