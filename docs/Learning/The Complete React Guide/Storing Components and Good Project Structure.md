---
tags:
  - react
  - components
  - structures
  - practice
  - project
---
# Storing Components and Good Project Structure


![[Pasted image 20231216171042.png]]

```jsx
import { CORE_CONCEPTS } from "./data.js";
import Header from "./components/Header.jsx";
import CoreConcept from "./components/CoreConcept.jsx";

function App() {
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
			</main>
		</div>
	);
}

export default App;

```

```jsx
import PropTypes from "prop-types";

CoreConcept.propTypes = {
	title: PropTypes.string,
	description: PropTypes.string,
	image: PropTypes.string,
};

export default function CoreConcept({ image, title, description }) {
	return (
		<li>
			<img src={image} alt={title} />
			<h3>{title}</h3>
			<p>{description}</p>
		</li>
	);
}

```

* The CSS file should also be split across multiple files, stored next to their respective components and not in 1 large index.css
* Importing a CSS file within a component will not scope these styles to that component.
* If we would use a Header element elsewhere, those styles would also be applied elsewhere.

