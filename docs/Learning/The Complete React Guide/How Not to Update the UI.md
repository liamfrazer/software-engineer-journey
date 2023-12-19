---
tags:
  - react
  - function
  - update
---
# How Not to Update the UI

* By default, React components execute only once.
* You have to "tell" React if a Component should be executed again

## How React Checks If UI updates are needed
* React compares the old output ("old JSX Code") of your component function to the new output ("new JSX code") and applies any differences to the actual website UI

* Updating the UI with a regular value will not work, as the function has already been executed and will not execute again.