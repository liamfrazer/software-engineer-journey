---
tags:
  - AI-ChatBot
  - routes
  - useLayoutEffect
---
# Chat Route to see previous chat

```jsx
// routes - chat.routes.ts
chatRoutes.get("/all-chats", verifyToken, sendChatsToUser);
```
```jsx
// helpers - api-communicator.ts
const getUserChats = async () => {
	const res = await axios.get("/chat/all-chats");
	if (res.status !== 200) {
		console.log(res.data);
		throw new Error(`Unable to send chat`);
	}
	const data = await res.data;
	return data;
};
```
```jsx
// controllers - chat-controllers.ts
export const sendChatsToUser = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const user = await User.findById(res.locals.jwtData.id);
		if (!user) {
			return res.status(401).send("User not found or Token malfunctioned");
		}
		if (user._id.toString() !== res.locals.jwtData.id) {
			return res.status(401).send("Permissions did not match");
		}

		return res.status(200).json({ message: "OK", chats: user.chats });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};

```
```jsx
// pages - Chat.tsx
	useLayoutEffect(() => {
		if (auth?.isLoggedIn && auth?.user) {
			toast.loading("Loading chats", { id: "loadchats" });
			getUserChats()
				.then((data) => {
					setChatMessages([...data.chats]);
					toast.success("Successfully loaded chats", { id: "loadchats" });
				})
				.catch((error) => {
					console.log(error);
					toast.error("Failed to load chats", { id: "loadchats" });
				});
		}
	}, [auth]);
```

