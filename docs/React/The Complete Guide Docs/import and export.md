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

* 