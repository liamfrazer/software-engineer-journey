---
tags:
  - react
  - APIs
  - useImperativeHandle
  - hooks
---
# Exposing  Component APIs via the useImperativeHandle Hook

* Majority of the time we will not require the useImperativeHandle hook, but in certain usecases where I require to expose the component to be more stable and usable

* We're passing the dialog as a value to the ResultModal
```jsx
<ResultModal ref={dialog} targetTime={targetTime} result="lost" />
```
* Thanks to `forwardRef` and `useImperativeHandle` the connection to the object is established
```jsx
const ResultModal = forwardRef(function ResultModal({ result, targetTime }, ref) {
	const dialog = useRef();

	useImperativeHandle(ref, () => {
		return {
			open() {
				dialog.current.showModal();
			},
		};
	});
```

* The open method from the `useImperativeHandle` object is now called
```jsx
	const handleStart = () => { timer.current = setTimeout(() => {
			setTimerExpired(true);
			dialog.current.open();
		}, targetTime * 1000);

		setTimerStarted(true);
	};
```