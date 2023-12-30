---
tags:
  - Node
  - Express
  - TypeScript
---
# Setup Node Express App with TypeScript

```jsx
import express from "express";

const app = express();

// GET -
// PUT -
// POST -
// DELETE -

app.get("/", (req, res, next) => {});

app.listen(5000, () => {
	console.log("Listening on port 5000");
});
```

```jsx
app.get("/", (req, res, next) => {});
```
* / is the location or URL that the GET request would be accessed from, in our example it will just be the main URL
* next is used to move on top the next middleware

![[Pasted image 20231230104337.png]]

* POST is used to send some data along with the request