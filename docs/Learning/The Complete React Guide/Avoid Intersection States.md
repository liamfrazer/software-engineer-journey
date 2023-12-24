---
tags:
  - intersecting
  - statements
  - react
  - jsx
---
# Avoid Intersection States
* You want to avoid managing the same data with multiple states
* It makes more sense to lift up the existing state into the parent component, which has both access to the Log component and the Gameboard component
* We can manage the information that we need for the clicks selected, as well as managing the order of clicks selected within the Log component all from the parent component


* We want to update the new turns, in front of the old turns, so that the first item in the array is the latest turn.
* We also want to ensure that when setting the `setGameTurns` state, that we're doing this correctly with the arrow function.

```jsx
	const handleSelectSquare = (rowIndex, colIndex) => {
		setActivePlayer((currentPlayer) => (currentPlayer === "X" ? "0" : "X"));
		setGameTurns((prevTurns) => {
			let currentPlayer = "X";
			if (prevTurns.length > 0 && prevTurns[0].player === "X") {
				currentPlayer = "0";
			}
			const updatedTurns = [
				{ square: { rowIndex, colIndex }, player: currentPlayer },
				...prevTurns,
			];

			return updatedTurns;
		});
	};
```
* The above updateState function is ensuring that we're upda