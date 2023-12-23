---
tags:
  - state
  - repetition
  - react
  - jsx
---
# Concept Repetition - Working with State

```jsx
import { useState } from "react";

const Player = ({ name, symbol }) => {
	const [isEditing, setIsEditing] = useState(false);

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

