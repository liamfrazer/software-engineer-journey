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
* 