---
tags:
  - CSS
  - react
  - Style
  - dynamic
---
# CSS Styling and Dynamic Styling

* React requires the use of `className` to set CSS styles
* This can be handled both with props and state

```jsx
import PropTypes from "prop-types";
export default function TabButton({ children, onSelect, isSelected }) {
	return (
		<li>
			<button className={isSelected ? "active" : ""} onClick={onSelect}>
				{children}
			</button>
		</li>
	);
}

TabButton.propTypes = {
	children: PropTypes.any,
	onSelect: PropTypes.func,
	isSelected: PropTypes.bool,
};

```

```jsx
					<menu>
						<TabButton
							isSelected={selectedTopic === "components"}
							onSelect={() => handleSelect("components")}
						>
							Components
						</TabButton>
						<TabButton
							isSelected={selectedTopic === "jsx"}
							onSelect={() => handleSelect("jsx")}
						>
							JSX
						</TabButton>
						<TabButton
							isSelected={selectedTopic === "props"}
							onSelect={() => handleSelect("props")}
						>
							Props
						</TabButton>
						<TabButton
							isSelected={selectedTopic === "state"}
							onSelect={() => handleSelect("state")}
						>
							State
						</TabButton>
					</menu>
```

```jsx
import React from 'react';

export default function App() {
    
    const [selected, setSelected] = React.useState();
    
    const handleClick = () => {
        setSelected(true);
    };
    
    
    return (
        <div>
            <p className={selected ? 'active' : ''}>Style me!</p>
            <button onClick={handleClick}>Toggle style</button>
        </div>
    );
}
```

