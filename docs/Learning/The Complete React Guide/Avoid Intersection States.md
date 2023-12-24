---
tags:
  - intersecting
  - statements
  - react
  - jsx
---
# Avoid Intersection States
* You want to avoid managing the same data with multiple states
* It makes more sense to lift up the existing state into the parent component, which has both access to the Log component and the Gameboard component
* We can manage the information that we need for the clicks selected, as well as managing the order of clicks selected within the Log component all from the parent component


* We want to update the new turns, in front of the old turns, so that the first item in the array is the latest turn.
* We also want to e