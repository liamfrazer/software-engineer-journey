---
tags:
  - updating
  - objects
  - state
  - immutably
  - react
  - jsx
  - spread
  - deep
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

* The above functionality is not recommended

* Objects & Arrays are reference values in JavaScript
* You should there not mutate them directly, instead create a (deep) copy first

```jsx
// wrong
const updatedUser = user;
user.name = "Liam" // Editing the user object in memory
```

```jsx
// correct
const updatedUSer = {...user}
updatedUser.name = "Liam"  Creating a copy via JavaScript's "Spread" operator
// Editing the copy, not the original
```

* If we followed the code above, we would be updating the object in memory, even before the state had been changed by React
* This can lead to strange bugs or side effects when multiple places schedule state updates for the same state


```jsx
	const handleSelectSquare = (rowIndex, colIndex) => {
		setGameBoard((prevGameBoard) => {
			const updatedBoard = [
				...prevGameBoard.map((innerArray) => [...innerArray]),
			];
			updatedBoard[rowIndex][colIndex] = "X";
			return updatedBoard;
		});
	};
```


