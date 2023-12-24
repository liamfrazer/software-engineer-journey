---
tags:
  - lists
  - multi-dimenstional
  - rendering
  - react
  - jsx
---
# Rendering Multi-dimensional Lists

```jsx
const initialGameBoard = [
	[null, null, null],
	[null, null, null],
	[null, null, null],
];

const GameBoard = () => {
	return (
		<ol id="game-board">
			{initialGameBoard.map((row, rowIndex) => (
				<li key={rowIndex}>
					<ol>
						{row.map((playerSymbol, colIndex) => (
							<li key={colIndex}>
								<button>{playerSymbol}</button>
							</li>
						))}
					</ol>
				</li>
			))}
		</ol>
	);
};
export default GameBoard;

```

