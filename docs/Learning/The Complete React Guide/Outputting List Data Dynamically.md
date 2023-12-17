---
tags:
  - dynamic
  - react
  - jsx
  - output
---
# Outputting List Data Dynamically
* Currently in our code, we're manually repeating components, which is against the DRY principles
* If we remove an entry, this breaks the app as we've still got a manual component being output.
* It would be better if we dynamically render components depending on how much data there is

* You can output an array of data within JSX
* You can also output an array of JSX elements
* The map item can be used, as the function would now output an item for every item that exists within the array

* 