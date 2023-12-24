---
tags:
  - updating
  - objects
  - state
  - immutably
  - react
  - jsx
---
# Updating Object State Immutably

```jsx
	const handleSelectSquare = (rowIndex, colIndex) => {
		setGameBoard((prevGameBoard) => {
			prevGameBoard[rowIndex][colIndex] = "X";
			return prevGameBoard;
		});
	};
```

