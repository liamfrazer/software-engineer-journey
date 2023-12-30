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

```jsx
app.use(express.json());
```
* This tells the application that we will be using JSON as the incoming and outgoing requests as JSON

```jsx
app.post("/", (req, res, next) => {
	console.log(req.body.name);

	return res.send("Hello");
});


```

![[Pasted image 20231230104836.png]]
![[Pasted image 20231230104846.png]]

* PUT request is sending data directly from the front end
```jsx
app.put("/", (req, res, next) => {
	console.log(req.body.name);

	return res.send("Hello");
});
```

* While we're only using a static route at the moment, there will be points in the future where we may have multiple users requiring the express server at the same time
* We could send the user ID within JSON to identify 
* We could send the ID into the URL as a dynamic route

## Dynamic Routing
```jsx
app.put("/user/:id", (req, res, next) => {
	console.log(req.params.id);

	return res.send("Hello");
});
```
![[Pasted image 20231230105726.png]]
![[Pasted image 20231230105738.png]]

![[Pasted image 20231230110121.png]]

```jsx
import express from "express";

const app = express();

// Middleware
app.use(express.json());

// Connection and Listener
app.listen(5000, () => {
	console.log("Listening on port 5000");
});

```

