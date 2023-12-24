---
tags:
  - state
  - props
  - react
  - jsx
  - components
---
# Deriving State From Props

* Instead of updating state in the code below, we're deriving state instead
* `gameBoard` is a computed value that is derived from the `gameTurns` state
* You should manage as little state as needed and derive as much as possible.

```jsx
const GameBoard = ({ onSelectSquare, turns }) => {
	let gameBoard = initialGameBoard;

	for (const turn of turns) {
		const { square, player } = turn;
		const { row, col } = square;

		gameBoard[row][col] = player;
	}
```

```jsx
<GameBoard onSelectSquare={handleSelectSquare} turns={gameTurns} />
```