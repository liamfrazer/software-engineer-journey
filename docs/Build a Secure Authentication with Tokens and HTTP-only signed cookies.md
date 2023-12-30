---
tags:
  - AI-ChatBot
  - Secure
  - Tokens
  - HTTP-only
  - models
  - Mongoose
---
# Build a Secure Authentication with Tokens and HTTP-only signed cookies
```jsx
import morgan from "morgan";
// Remove from Production
app.use(morgan("dev"));
```

```jsx
import { Router } from "express";
import userRoutes from "./user.routes.js";
import chatRoutes from "./chat.routes.js";

const appRouter = Router();

appRouter.use("/user", userRoutes); // domain/api/v1/user
appRouter.use("/chat", chatRoutes); // domain/api/v1/chat

export default appRouter;

```

```jsx
import { Router } from "express";

const chatRoutes = Router();

export default chatRoutes;

```

```jsx
import { Router } from "express";
import getAllUsers from "../controllers/user-controllers.js";

const userRoutes = Router();

userRoutes.get("/", getAllUsers);

export default userRoutes;

```

## Database Models

```jsx
import mongoose from "mongoose";
import { randomUUID } from "crypto";

const chatSchema = new mongoose.Schema({
	id: {
		type: String,
		default: randomUUID,
		role: { type: String, required: true },
		content: {
			type: String,
			required: true,
		},
	},
});

const userSchema = new mongoose.Schema({
	name: {
		type: String,
		required: true,
	},
	email: {
		type: String,
		required: true,
		unique: true,
	},
	password: {
		type: String,
		required: true,
	},
	chats: [chatSchema],
});

export default mongoose.model("User", userSchema);

```

