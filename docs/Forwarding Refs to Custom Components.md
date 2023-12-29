---
tags:
  - react
  - useRef
  - components
---
# Forwarding Refs to Custom Components
```jsx
	const dialog = useRef(null);
	<ResultModal ref={dialog} targetTime={targetTime} result="lost" />
	export const ResultModal = ({ result, targetTime, ref }) => {


	dialog.current.showModal();
```

* We can't forward a ref to another component as it will appear as a prop that doesn't exist

* We need to use a special function provided by React
```jsx
import { forwardRef } from "react";
```

