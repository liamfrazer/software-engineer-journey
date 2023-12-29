---
tags:
  - react
  - useRef
  - useState
---
# Refs vs State Values

* When trying to access the `useRef()` when the component has been rendered for the first time, this will not work and using `useState()` is still required

* Whenever a ref changes, the component function does not re-execute
* Whenever a state changes, the component function will be re-executed


## State
* Causes component re-evaluation (re-execution) when changed
* Should be used for values that are directly reflected in the UI
* Should not be used for "behind the scenes" values that have no direct UI impact

## Refs
* Do not cause component re-evaluation
* Can be used to gain direct DOM element access
* Great for reading values or accessing certain browser APIs

