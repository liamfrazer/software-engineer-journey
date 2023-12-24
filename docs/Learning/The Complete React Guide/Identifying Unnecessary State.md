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

* We're still grabbing the activePlayer, but now we're doing it without managing additional states that we don't have to

* In React, you want to manage as little or as few states as possible, and then derive as many values as needed