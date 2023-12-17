---
tags:
  - events
  - functions
  - custom
  - arguments
  - react
---
# Passing Custom Arguments to Event Functions


* We'll need to know which button was clicked

```jsx
import { CORE_CONCEPTS } from "./data.js";
import Header from "./components/Header/Header.jsx";
import CoreConcept from "./components/CoreConcept/CoreConcept.jsx";
import TabButton from "./components/TabButton/TabButton.jsx";

function App() {
	const handleSelect = (selectedButton) => {
		// selectedButton => 'components', 'jsx', 'props', 'state'
		console.log("Selected");
	};
	return (
		<div>
			<Header />
			<main>
				<section id="core-concepts">
					<h2>Core Concepts</h2>
					<ul>
						<CoreConcept {...CORE_CONCEPTS[0]} />
						<CoreConcept {...CORE_CONCEPTS[1]} />
						<CoreConcept {...CORE_CONCEPTS[2]} />
						<CoreConcept {...CORE_CONCEPTS[3]} />
					</ul>
				</section>
				<section id="examples">
					<h2>Examples</h2>
					<menu>
						<TabButton onSelect={handleSelect}>
							Components
						</TabButton>
						<TabButton onSelect={handleSelect}>JSX</TabButton>
						<TabButton onSelect={handleSelect}>Props</TabButton>
						<TabButton onSelect={handleSelect}>State</TabButton>
					</menu>
				</section>
			</main>
		</div>
	);
}

export default App;

```

* By default in the code above, we are not getting the identify of which button was clicked
* We will have to control how handleSelect is used.
* Instead of passing `handleSelect` as a value, we can instead pass an arrow function to `onSelect`
* Anonymous arrow functions can be passed like the below

```jsx
						<TabButton onSelect={() => handleSelect()}>
							Components
						</TabButton>
```

