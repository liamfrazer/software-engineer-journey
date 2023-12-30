---
tags:
  - MongoDB
  - Mongoose
  - AI-ChatBot
---
# Integrate MongoDB Database Connection
![[Pasted image 20231230111022.png]]
```jsx
import { config } from "dotenv";
config();
```
![[Pasted image 20231230111336.png]]
```jsx
// app.ts
import express from "express";
import { config } from "dotenv";
config();

const app = express();

// Middleware
app.use(express.json());

export default app;


```

```jsx
// index.ts
import app from "./app.js";
import { connectToDatabase } from "./db/connection.js";

const PORT = process.env.port || 5000;

// Connection and Listener
connectToDatabase()
	.then(() => {
		app.listen(PORT, () => {
			console.log("Server open & connected to MongoDB");
		});
	})
	.catch((err) => {
		console.log(err);
	});

```
```jsx
// Server open & connected to MongoDB
```

