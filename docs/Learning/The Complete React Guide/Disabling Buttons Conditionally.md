---
tags:
  - buttons
  - conditional
  - jsx
  - react
---
# Disabling Buttons Conditionally

```jsx
<button onClick={() =>	onSelectSquare(rowIndex, colIndex)} disabled={playerSymbol}	>
	{playerSymbol}
</button>
```

* If `playerSymbol` is a false value, this means that the `disabled` prop will not be set
* If `playerSymbol` is a true value, which means the symbol has been selected by a player, this then means that the disable option will then be set, preventing the button from being clicked again.


