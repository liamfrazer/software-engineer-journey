---
tags:
  - AI-ChatBot
  - Secure
  - Tokens
  - HTTP-only
  - models
  - Mongoose
  - Middleware
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

## Getting all users from the database

```jsx
import { Request, Response, NextFunction } from "express";
import User from "../models/User.js";

const getAllUsers = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const users = await User.find();
		return res.status(200).json({ message: "OK", users });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};

export default getAllUsers;

```

```jsx
// [1] GET /api/v1/user 200 32.896 ms - 27
```
![[Pasted image 20231230123310.png]]

## Signup process and encrypting passwords

```jsx
import { Request, Response, NextFunction } from "express";
import { hash } from "bcrypt";
import User from "../models/User.js";

const getAllUsers = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const users = await User.find();
		return res.status(200).json({ message: "OK", users });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};

const userSignUp = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const { name, email, password } = req.body;
		const hashedPassword = await hash(password, 10);
		const user = new User({ name, email, hashedPassword });
		await user.save();
		return res.status(200).json({ message: "OK", id: user._id.toString() });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};

export { getAllUsers, userSignUp };

```

```jsx
// POST /api/v1/user/signup 200 86.516 ms - 48
```
![[Pasted image 20231230125213.png]]
![[Pasted image 20231230125245.png]]

```json
{
    "message": "OK",
    "users": [
        {
            "_id": "659012136e04c2fa96a1a5a0",
            "name": "Liam",
            "email": "liam.frazer@gmail.com",
            "password": "$2b$10$EbD.7KUwZmKe89GMf.n4nek8WlZNjpa9wrZsHpRWlh3sgZ4bvgmMu",
            "chats": [],
            "__v": 0
        }
    ]
}
```

## Middlewares
* Middleware are functions which get executed before a request is processed.
* In Node and Express, middleware can be used to check JSON body validations, Tokens or Cookie Validations, Params Validations and more according to specific requirements

![[Pasted image 20231230130914.png]]

## Validation middleware with express-validator

```jsx
import { body, ValidationChain, validationResult } from "express-validator";
import { Request, Response, NextFunction } from "express";

const validate = (validations: ValidationChain[]) => {
	return async (req: Request, res: Response, next: NextFunction) => {
		for (let validation of validations) {
			const result = await validation.run(req);
			if (!result.isEmpty()) {
				break;
			}
		}
		const errors = validationResult(req);
		if (errors.isEmpty()) {
			return next();
		}
		return res.status(422).json({ errors: errors.array() });
	};
};

const signupValidator = [
	body("name").notEmpty().withMessage("Name is required"),
	body("email").trim().isEmail().withMessage("Email is required"),
	body("password")
		.trim()
		.isLength({ min: 6 })
		.withMessage("Password should contain at least 6 characters"),
];

export { validate, signupValidator };

```

```jsx
userRoutes.post("/signup", validate(signupValidator), userSignup);
```
```json
{
    "errors": [
        {
            "type": "field",
            "value": "liam",
            "msg": "Email is required",
            "path": "email",
            "location": "body"
        }
    ]
}
```
```console
POST /api/v1/user/signup 422 3.406 ms - 103
```

```json
"errors": [
        {
            "type": "field",
            "value": "12345",
            "msg": "Password should contain at least 6 characters",
            "path": "password",
            "location": "body"
        }
    ]
}
```
```console
POST /api/v1/user/signup 422 1.491 ms - 135
```

## Login Functionality

```json
{
    "message": "OK",
    "id": "65901f7bacad39432540b36c"
}
```
```console
[1] POST /api/v1/user/login 200 83.719 ms - 48
```

```jsx
const loginValidator = [
	body("email").trim().isEmail().withMessage("Email is required"),
	body("password")
		.trim()
		.isLength({ min: 6 })
		.withMessage("Password should contain at least 6 characters"),
];

const signupValidator = [
	body("name").notEmpty().withMessage("Name is required"),
	...loginValidator,
];

export { validate, signupValidator, loginValidator };

```
```jsx
const userLogin = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const { email, password } = req.body;
		const user = await User.findOne({ email });
		if (!user) {
			return res.status(401).send("User not found");
		}
		const isPasswordCorrect = await compare(password, user.password);
		if (!isPasswordCorrect) {
			return res.status(403).send("Invalid credentials");
		}
		return res.status(200).json({ message: "OK", id: user._id.toString() });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};
```





