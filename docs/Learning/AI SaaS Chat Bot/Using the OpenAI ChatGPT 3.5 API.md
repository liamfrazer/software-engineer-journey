---
tags:
  - AI-ChatBot
  - react
  - ChatGPT
  - APIs
---
# Using the OpenAI ChatGPT 3.5 API

```jsx
// routes - chat.routes.ts
import { Router } from "express";
import { verifyToken } from "../utils/token-manager.js";
import { validate, chatCompletionValidator } from "../utils/validators.js";
import { generateChatCompletion } from "../controllers/chat-controllers.js";

// Protected API
const chatRoutes = Router();
chatRoutes.post("/new", validate(chatCompletionValidator), verifyToken, generateChatCompletion);

export default chatRoutes;

```
```jsx
// controllers - chat-controllers.ts
import { Request, Response, NextFunction } from "express";
import { configureOpenAI } from "../config/openai-config.js";
import { OpenAIApi, ChatCompletionRequestMessage } from "openai";
import User from "../models/User.js";

const generateChatCompletion = async (req: Request, res: Response, next: NextFunction) => {
	const { message } = req.body;
	try {
		const user = await User.findById(res.locals.jwtData.id);
		if (!user) {
			return res.status(401).json({ message: "User not registered or Token malfunctioned" });
		}
		// Grab chats from User
		const chats = user.chats.map(({ role, content }) => ({ role, content })) as ChatCompletionRequestMessage[];
		chats.push({ content: message, role: "user" });
		user.chats.push({ content: message, role: "user" });
		// Send all chats with new one to OpenAI API
		const config = configureOpenAI();
		const openAI = new OpenAIApi(config);
		// Get response from OpenAI
		const chatResponse = await openAI.createChatCompletion({ model: "gpt-3.5-turbo", messages: chats });
		user.chats.push(chatResponse.data.choices[0].message);
		await user.save();
		return res.status(200).json({ chats: user.chats });
	} catch (error) {
		console.log(error);
		return res.status(500).json({ message: "Something went wrong" });
	}
};

export { generateChatCompletion };

```
```jsx
// Utils - validators.ts
const chatCompletionValidator = [body("name").notEmpty().withMessage("Message is required")];
```
```jsx
// config - openai-config.ts
import { Configuration } from "openai";

const configureOpenAI = () => {
	const config = new Configuration({
		apiKey: process.env.OPEN_AI_SECRET,
		organization: process.env.OPEN_AI_ORGANIZATION_ID,
	});
	return config;
};

export { configureOpenAI };

```
