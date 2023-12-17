---
tags:
  - react
  - state
  - hooks
  - managing
---
# Managing State and Using Hooks

* We cannot use a regular variable for updating the UI
* We need to tell React we want to update the UI

```jsx
import { useState } from "react";
```
* This is a React hook, any function starting with `use` are React Hooks
* Hooks are regular functions, but only to be called within Components or other Hooks
* `useState()` must be used within the top level of the component and cannot be called within a Function.

## Rules of Hooks
* Only call Hooks inside of Component Functions
	* React Hooks must not be called outside of React component functions
* Only call Hooks on the top level
	* React Hooks must not be called in nested code statements (e.g inside of if-statements)

* useState() is the most important function built into React
* useState does accept an argument, which is the default value you want React to store/use


* `useState()` contains an Array with two elements
* It will always be two elements

```jsx
    const [selectedTopic, setSelectedTopic] = useState("Please click a button:");
```

![[Pasted image 20231217150957.png]]

* Manage data & "tell" React to re-execute a component function via React's `useState()` Hook
* State updates lead to new state values (as the component function executes again)

* Calling the `setCounter` special function within the example above, will then allow the Component where the state is stored to be re-rendered
* In the example above, counter will be re-created each time the component function executes, this means that we're able to use a const

* When you call `setSelectedTopic`, React schedules the state update and then re-executes the Component Function. Therefore, the updated value is only available once the Component Function has been re-rendered.
* 

