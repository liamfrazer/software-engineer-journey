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

