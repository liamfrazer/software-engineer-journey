---
tags:
  - react
  - jsx
  - slots
---
# Working with Multiple JSX Slots

* The idea behind the Tabs component is that we could use it for all types of Tabs
* This means that we don't want to manage the content directly within the Tabs component, it should be managed where it is used

```jsx
				<TabButton
					isSelected={selectedTopic === "components"}
					onClick={() => handleSelect("components")}
				>
```

* There will be two issues with moving the TabButton into a Tabs component
* We want to use both the isSelected and the onClick function detected by clicking this component

* We don't want to accept a bunch of props just to get the buttons to work
* Instead, we can pass the buttons as JSX code to the Tabs element
* We want to have an additional slot for JSX code within the Tabs component

* JSX elements are just regular values and can be used like values
* 

