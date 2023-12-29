---
tags:
  - react
  - portals
---
# Detaching DOM Rendering from JSX Structure with Portals
* Technically, it would make more sense for the overlay element to be output directly within a body or a `div`
* A deeply nested element could be hidden by other elements

```jsx
import { createPortal } from "react-dom";
```
* The idea is to teleport the HTML code into a different place within the DOM
* This wraps the returned JSX and then a second value is passed from the main HTML file

```jsx
	return createPortal(
		<dialog ref={dialog} className="result-modal" onClose={onReset}>
			{userLost && <h2>You lost.</h2>}
			{!userLost && <h2>Your Score: {score}</h2>}
			<p>
				The target time was <strong>{targetTime} seconds.</strong>
			</p>
			<p>
				You stopped the timer with{" "}
				<strong>{formattedRemainingTime} seconds left.</strong>
			</p>
			<form method="dialog" onSubmit={onReset}>
				<button>Close</button>
			</form>
		</dialog>,
		document.getElementById("modal")
	);
```



