---
tags:
  - react
  - components
  - props
  - reusable
  - destructuring
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

* PropTypes

```jsx
import PropTypes from "prop-types";

CoreConcept.propTypes = {
	title: PropTypes.string,
	description: PropTypes.string,
	image: PropTypes.string,
};


```

* Thanks to props, is that the component is re-usable

* We can use a shorthand spread operator to pull out all the key value pairs of an object.
* By using the spread operator, key value pairs of the object can be added as key value pairs to the component as props.

```jsx
function App() {
	return (
		<div>
			<Header />
			<main>
				<section id="core-concepts">
					<h2>Core Concepts</h2>
					<ul>
						<CoreConcept {...CORE_CONCEPTS[0]} />
						<CoreConcept {...CORE_CONCEPTS[1]} />
						<CoreConcept {...CORE_CONCEPTS[2]} />
						<CoreConcept {...CORE_CONCEPTS[3]} />
					</ul>
				</section>
			</main>
		</div>
	);
}

export default App;
```

* The alternative is fine, but you may want to go with a shorter alternative

* Within the parameter list, we can use object destructuring 
* When using destructuring, JavaScript will match the properties coming out of the object as standalone variables within the function.
* Object destructuring can be used with either longhand or shorthand objects on the component itself.

```jsx
function CoreConcept({ image, title, description }) {
	return (
		<li>
			<img src={image} alt={title} />
			<h3>{title}</h3>
			<p>{description}</p>
		</li>
	);
}
```

### Default prop values
* Sometimes, you'll build components that may receive an optional prop.
* For example, a custom `button` component may receive a `type` prop.
* So the button component should be usable either with a type being set:
```jsx
<Button type="submit" caption="My Button" />
```
* Or Without
```jsx
<Button caption="My Button"
```
* To make this component work, you might want to set a default value for the type prop, in case it's not passed.
* This can easily be achieved since JavaScript supports default values when using object destructuring:
```jsx
export default function Button({ caption, type = "submit"}) {
//caption has no default value, type has a default value of "submit"
}
```

