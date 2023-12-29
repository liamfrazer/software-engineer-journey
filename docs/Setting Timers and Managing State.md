---
tags:
  - react
  - useRef
  - useState
  - timers
---
# Setting Timers and Managing State
* Whenever we're updating state, we have to remember that the state will cause the component to be re-evaluated/re-rendered - this means that if we set a timer as a variable, once the refresh takes places this essentially will be a new timer variable

* Moving this outside of the component will also not resolve the issue
* Doing the above will cause the variable to be shared across multiple instances


```jsx
import { useState, useRef } from "react";

export const TimerChallenge = ({ title, targetTime }) => {
	const [timerStarted, setTimerStarted] = useState(false);
	const [timerExpired, setTimerExpired] = useState(false);

	let timer;
	const handleStart = () => {
		timer = setTimeout(() => {
			setTimerExpired(true);
		}, targetTime * 1000);

		setTimerStarted(true);
	};

	const handleStop = () => {
		clearTimeout(timer);
	};

	return (
		<section className="challenge">
			<h2>{title}</h2>
			{timerExpired && <p>Timer Expired</p>}
			<p className="challenge-time">
				{targetTime} second{targetTime > 1 ? "s" : ""}
			</p>
			<p>
				<button onClick={timerStarted ? handleStop : handleStart}>
					{timerStarted ? "Stop" : "Start"} Challenge
				</button>
			</p>
			<p className={timerStarted ? "active" : ""}>
				{timerStarted ? "Time is running" : "Timer inactive"}
			</p>
		</section>
	);
};

```

* Instead we can use `useRef()` which will allow React to store these values behind the scene and will also not be re-rendered/modified whenever the state changes


```jsx

```