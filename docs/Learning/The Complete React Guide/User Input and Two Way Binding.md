---
tags:
  - react
  - user
  - input
  - binding
  - jsx
---
# User Input and Two Way Binding
* The value prop sets the value shown within the input
```jsx
	if (isEditing) {
		playerName = <input type="text" value={name} required />;
	}
```

* Using `onChange={handleChange}` within an input field will trigger for every keystoke
* It will provide us with an event object that contains the value entered by the user
* React will call the `handleChange` function, when the change occurs and React will provide the event object as an argument for the function
* 