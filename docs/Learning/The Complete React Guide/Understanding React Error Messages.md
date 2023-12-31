---
tags:
  - react
  - error
  - messages
---
# Understanding React Error Messages
![[Pasted image 20231228175813.png]]

* Uncaught TypeError: results[0] is undefined

![[Pasted image 20231228180152.png]]

```jsx
 for (let i = 0; i < duration; i++) {
    const interestEarnedInYear = investmentValue * (expectedReturn / 100);
    investmentValue += interestEarnedInYear + annualInvestment;
    results.push({
      year: i + 1, // year identifier
      interest: interestEarnedInYear, // the amount of interest earned in this year
      valueEndOfYear: investmentValue, // investment value at end of year
      annualInvestment: annualInvestment, // investment added in this year
    });
  }
}
```

```jsx
	if (results.length < 1) {
		return <p>Duration cannot be less than 0</p>;
	}
```

![[Pasted image 20231228181412.png]]
## Strict mode
```jsx
import { StrictMode } from 'react';
<StrictMode>
	<App />
</StrictMode>
```

* When every component gets executed twice, it helps capture duplication errors, e.g. twice the amount of variables within a table
* It immediately shows when there could be a problem

## React Devtools

![[Pasted image 20231228182501.png]]

