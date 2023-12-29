---
tags:
  - react
  - refs
---
# What are Refs
* A `ref` in React is a value, similar to how a variable or state is a value
* It's a value managed by React

```jsx
import { useState } from "react";
export default function Player() {
	const [enteredPlayerName, setEnteredPlayerName] = useState(null);
	const [submitted, setSubmitted] = useState(false);

	const handleChange = (event) => {
		setSubmitted(false);
		setEnteredPlayerName(event.target.value);
	};

	const handleClick = () => {
		setSubmitted(true);
	};

	return (
		<>
			<section id="player">
				<h2>
					Welcome {submitted ? enteredPlayerName : "unknown entity"}
				</h2>
				<p>
					<input
						type="text"
						onChange={handleChange}
						value={enteredPlayerName}
					/>
					<button onClick={handleClick}>Set Name</button>
				</p>
			</section>
		</>
	);
}

```

* All hook functions must be called inside of a component function
* You can connect them to JSX elements, with a special prop `ref`
* `ref` is a prop that can be added to any JSX element
* `ref` takes a special value

```jsx
import { useState, useRef } from "react";

const playerName = useRef(null);

<input ref={playerName} type="text" onChange={handleChange} value={enteredPlayerName}/>
```

* The `ref` value will usually always be a JavaScript object that will always have a `current` property
* Within the current property, the connected input will be stored

![[Pasted image 20231229101126.png]]

