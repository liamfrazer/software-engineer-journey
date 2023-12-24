---
tags:
  - react
  - state
  - updating
  - correctly
---
# Updating State Based on Old State Correctly

* In React, when updating state based on the previous value of the state, you should not use something like `setIsEditing(!isEditing)`
* Instead, you should pass a function to the `setIsEditing` function

* If your new state depends on your previous state value, you should not update the state like this.
* Instead, pass a function to your state updating function
* This function will automatically be called by React and will receive the guaranteed latest state value

## React is scheduling State Updates
* State updates are not performed instantly but at some point in the future, when React has time for it
* In most cases, those state updates are still executed almost instantly
* By adding a function, you're guaranteed by React to always be working with the latest state update
* 
