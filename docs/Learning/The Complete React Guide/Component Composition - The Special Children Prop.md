---
tags:
  - react
  - components
  - composition
  - children
  - props
---
# Component Composition - The Special Children Prop


* If I pass something between opening component and closing component tags, the content is not output on the page. React doesn't know where to output the code.
* Even if you're not setting any attributes, React will still continue to give you the `props` object, it will be pretty empty, but not completely empty.
* You will always be passed the special built in `props.children`

* The `props.children` contains the content between component opening and closing tags, this is used as a value for the special `children` prop
* React automatically passes a special prop named `children` to every custom component


* The above feature is called Component Composition
* This approach depends on the exact usecase,
* On our button approach, Component Composition works well
* Both approaches work, but comes down to personal preference

* Children
	* For components that take a single piece of renderable content, this approach is closer to "normal HTML usage"
	* This approach is especially convenient when passing JSX code as a value to another component
* Attributes
	* This approach makes sense if you got multiple smaller pieces of information that must be passed to a component.
	* Adding extra props instead of just wrapping the content with the component tags mean extra work

* Both options come down to use-case and pe