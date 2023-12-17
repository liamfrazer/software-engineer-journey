---
tags:
  - props
  - functions
  - values
  - react
---
# Passing Functions as values to Props

* We want to update content whenever a button is pressed, then we want to show different content depending on which button was pressed

* In order to set dynamic content, we need to listen for clicks on our custom button
* Because you must handle the event in the component that also manages the data that should be changed
	* The "Dynamic Content" that should be displayed in this case

* Props that receive a function, should start with on
* This makes it clear that it's set to a function, depending on an event

```jsx
import { CORE_CONCEPTS } from "./data.js";
import Header from "./components/Header/Header.jsx";
import CoreConcept from "./components/CoreConcept/CoreConcept.jsx";
import TabButton from "./components/TabButton/TabButton.jsx";

function App() {
	const handleSelect = () => {
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

* We're passing a pointer at the handleSelect function, passing the function as a value to the onSelect prop, in our custom component, we're passing the function to the onClick prop, which then triggers the original function from the App.jsx file

* 