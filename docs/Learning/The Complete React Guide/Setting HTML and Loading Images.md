---
tags:
  - images
  - html
  - react
  - import
---
# Setting HTML and Loading Images

* When loading images directly in React, they should not be loaded via older HTML `img` tags
* This may get lost by React, or skipped by the React build stage

```jsx
import reactImg from ""
```

* The image is now a JavaScript variable that will include a path to the image
* This will also include an automatically generated path that will also work once deployed

```jsx
<img src={reactImg} alt="Stylized atom" />
```

* Quotes must be omitted, else this will be a string. They must also include the JSX `{}` to poin t at JavaScript values
