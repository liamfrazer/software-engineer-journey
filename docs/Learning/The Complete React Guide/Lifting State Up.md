---
tags:
  - lifting
  - state
  - update
  - components
  - jsx
  - react
---
# Lifting State Up

* We need to know the active player in both the GameBoard component and the Player component

* Lift the state up to the closest ancestor component that has access to all components that need to work with that state

```jsx
const [activePlayer, setActivePlayer] = useState("X");
```

```jsx
<GameBoard onSelectSquare={handleSelectSquare} activePlayerSymbol={activePlayer}/>
```

```jsx
const GameBoard = ({ onSelectSquare, activePlayerSymbol }) => {
	const [gameBoard, setGameBoard] = useState(initialGameBoard);
```

```jsx
updatedBoard[rowIndex][colIndex] = activePlayerSymbol;
return updatedBoard;
```

