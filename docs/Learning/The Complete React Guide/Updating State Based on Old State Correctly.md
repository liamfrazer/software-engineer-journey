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
* This function will automatically be called by React and wi