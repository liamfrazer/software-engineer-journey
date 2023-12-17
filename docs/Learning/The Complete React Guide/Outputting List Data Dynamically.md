---
tags:
  - dynamic
  - react
  - jsx
  - output
---
# Outputting List Data Dynamically
* Currently in our code, we're manually repeating components, which is against the DRY principles
* If we remove an entry, this breaks the app as we've still got a manual component being output.
* It would be better if we dynamically render components depending on how much data there is

* You can output an array of data within JSX
* You can also output an array of JSX elements
* The map item can be used, as the function would now output an item for every item that exists within the array

* In React, you will often lists of data and often create components from them.
* Majority of the time you will require the map method to do this.

* Each child in a list should have a unique key prop.
* We're not using the key prop, as it will be used by React

```jsx
				<section id="core-concepts">
					<h2>Core Concepts</h2>
					<ul>
						{CORE_CONCEPTS.map((conceptItem) => (
							<CoreConcept
								key={conceptItem.title}
								{...conceptItem}
							/>
						))}
					</ul>
				</section>
```

```jsx
import React from 'react';
import Todo from './Todo'
import './styles.css'

// don't remove the export keyword here!
export const DUMMY_TODOS = [
    'Learn React',
    'Practice React',
    'Profit!'
];

// don't change the Component name "App"
export default function App() {
    return(
        <ul>
            {DUMMY_TODOS.map(todo => <Todo text={todo} />)}
        </ul>
    );
}

```
```jsx
import React from 'react';

export default function Todo(props) {
    return <li>{props.text}</li>;
}
```
