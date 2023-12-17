---
tags:
  - react
  - events
---
# Reacting to Events

* As we're using react, we don't want to interact with the DOM ourselves, like we would in JavaScript
* Instead, we can use inbuilt elements with their built in props such as `onClick`

* Any event prop must be a function, as we want to point at the function that executes when the event occurs

* The advantage of defining these event handler functions inside the component function is that they then have access to the component's prop and state.

* Muse use the name as the function, as we want to use the function as a value
* This should not be executed with parenthesis
* Using the Function as a value means that the function is executed by React when a click on the button occurs.

```jsx
import PropTypes from "prop-types";
export default function TabButton({ children }) {
	const handleClick = () => {
		console.log(children);
	};

	return (
		<li>
			<button onClick={handleClick}>{children}</button>
		</li>
	);
}

TabButton.propTypes = {
	children: PropTypes.any,
};

```

