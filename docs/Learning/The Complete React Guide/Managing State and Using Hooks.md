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
	* React Hooks must not be called in nested code statements (e.g inside of if-s)

