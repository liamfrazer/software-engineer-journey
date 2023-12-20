---
tags:
  - react
  - state
  - Split
  - components
  - Feature
---
# Splitting Components by Feature and State

* Managing state within the main App component was causing the whole App component to re-run
* This was causing the `<Header />` component to re-run the random name function for the title.
* By moving the state to it's own component, this means that each time we do a re-render within select components, the App component does not cause additional code to re-run

* The app component will not be executed again, but instead, the Example function/component will be executed by itself
* 
