---
tags:
  - react
  - components
  - html
  - javascript
  - CSS
  - Declarative
---
# Creating Components
* Reusable Building Blocks
	* Create small building blocks & compose the UI from them
	* If needed, reuse a building block in different parts of the UI
* Related Coder Lives Together
	* Related HTML & JS & CSS code is stored together
	* Since JS influences the output, storing JS and HTML together makes sense
* Separation of Concerns
	* Different components handle different data & logic
	* Vastly simplifies the process of working on complex apps


## Describe the target UI with JSX
* JavaScript Syntax Extension
* Used to describe & create HTML elements in JavaScript in a declarative way.
* With React, you write declarative code
* You define the target HTML structure  & UI, not the steps to get there
* Browsers do not support JSX
* React projects come with a build process that transforms JSX

## Component Functions Rules
* Names starts with an Uppercase character
	* The function name must start with an uppercase character
	* Multi-word names should be written in PascalCase (e.g MyHeader)
	* It's recommended to pick a name that describes the UI building block
* Returns "Render able" Content
	* The function must return a value that can be rendered ("displayed on screen") by React
	* In most cases, return JSX, but allowed to return string, number, boolean, null, arrays


* Use the format document command/shortcut in VS code to auto-format your code.
* This does not just improve readability, but also adds the required wrapping parentheses.


* React component functions can be used like regular HTML
* 



