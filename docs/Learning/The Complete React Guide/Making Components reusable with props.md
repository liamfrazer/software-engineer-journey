---
tags:
  - react
  - components
  - props
  - reusable
---
# Making Components reusable with props

* Main advantage of components is that they're reusable
* You can reuse React components, but you don't have to.

* Like we can use functions with different data, we can also use components with different data


* React allows you to pass data to components via a concept called `Props`

* JSX Code that uses a Component > Set Props > Component > Receive Props > Component Function

* JSX Code that uses a Component
	* Set component input data via "custom HTML attributes (props)"
* Component
	* Defines internal logic + JSX code that should be rendered
* Component Function
	* Receives props with parameter with configuration data


* You're not limited to values when passing props.
* String/Number/Array/Object
* props is the name typically chosen
* Props will be set by React, as React will execute the function, we're using them as HTML elements


```jsx
						<CoreConcept
							title="Components"
							description="The Core UI building block."
							image={componentsImg}
						/>
						<CoreConcept />
						<CoreConcept />
						<CoreConcept />
```

```jsx
function CoreConcept(props) {
	return (
		<li>
			<img src={props.image} alt={props.title} />
			<h3>{props.title}</h3>
			<p>{props.description}</p>
		</li>
	);
}
```

![[Pasted image 20231216104945.png]]

