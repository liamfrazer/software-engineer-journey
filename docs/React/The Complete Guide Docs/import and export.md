---
tags:
  - import
  - export
  - javascript
---
# import and export

* Best practice to split code across multiple files, with import and export
* Adding `export` will allow variables/code to be available outside of the file it was created
* We should then `import` it in the locations where we require to use it

```js
export let apiKey = "apikey";
```
```js
import { apiKey } from "./utils";
```

* Majority of the time in React projects, the extension isn't required and will be omitted
* This will instead be handled by the build process behind the scenes

* **For the import and export keywords to function, we must ensure to use the type `module`**
* 
