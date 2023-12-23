---
tags:
  - state
  - repetition
  - react
  - jsx
---
# Concept Repetition - Working with State

* Original
```jsx
import { useState } from "react";

const Player = ({ name, symbol }) => {

	return (
		<li>
			<span className="player">
				<span className="player-name">{name}</span>
				<span className="player-symbol">{symbol}</span>
			</span>
			<button>Edit</button>
		</li>
	);
};

export default Player;

```

## My Edit

```jsx
import { useState } from "react";

const Player = ({ name, symbol }) => {
	const [isEditing, setIsEditing] = useState(false);
	const [playerName, setPlayerName] = useState(name);

	const handleClick = () => {
		setIsEditing(!isEditing);
	};

	const handleSubmit = (event) => {
		event.preventDefault();
		setIsEditing(!isEditing);
		console.log(playerName);
	};

	const handleInputChange = (event) => {
		setPlayerName(event.target.value);
	};

	if (isEditing) {
		return (
			<li>
				<form onSubmit={handleSubmit}>
					<input
						type="text"
						value={playerName}
						onChange={handleInputChange}
					/>
					<button type="submit">Save</button>
				</form>
			</li>
		);
	}

	return (
		<li>
			<span className="player">
				<span className="player-name">{playerName}</span>
				<span className="player-symbol">{symbol}</span>
			</span>
			<button onClick={() => handleClick()}>Edit</button>
		</li>
	);
};

export default Player;

```

## Course Edit
* We're passing the `handleEditClick` function as a value and not calling the function right away.
* Calling the `setIsEditing` function is changing a s
