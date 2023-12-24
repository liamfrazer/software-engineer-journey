---
tags:
  - state
  - react
  - components
---
# Identifying Unnecessary State

* Helper function that sits outside of the App function

```jsx
const deriveActivePlayer = (gameTurns) => {
	let currentPlayer = "X";
	if (gameTurns.length > 0 && gameTurns[0].player === "X") {
		currentPlayer = "0";
	}
	return currentPlayer;
};
```

