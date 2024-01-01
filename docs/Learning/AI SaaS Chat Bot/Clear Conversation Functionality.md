---
tags:
  - AI-ChatBot
---
# Clear Conversation Functionality
```jsx
// routes - chat.routes.ts
chatRoutes.delete("/delete", verifyToken, deleteChats);
```
```jsx
// pages - Chat.tsx
	const handleDeleteChats = async () => {
		try {
			toast.loading("Deleting chats", { id: "deletechats" });
			await deleteUserChats();
			setChatMessages([]);
			toast.success("Successfully deleted chat", { id: "deletechats" });
		} catch (error) {
			console.log(error);
			toast.success("Failed to delete chat", { id: "deletechats" });
		}
	};

					<Button onClick={handleDeleteChats} sx={{ width: "200px", my: "auto", color: "white", fontWeight: 700, borderRadius: 3, mx: "auto", bgcolor: red[300], ":hover": { bgcolor: red[400] } }}>
						Clear Conversation
					</Button>

```
```jsx
// helpers - api-communicator.ts
const deleteUserChats = async () => {
	const res = await axios.delete("/chat/delete");
	if (res.status !== 200) {
		console.log(res.data);
		throw new Error(`Unable to delete chat`);
	}
	const data = await res.data;
	return data;
};
```
```jsx
// controllers - chat-controllers.ts
export const deleteChats = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const user = await User.findById(res.locals.jwtData.id);
		if (!user) {
			return res.status(401).send("User not found or Token malfunctioned");
		}
		if (user._id.toString() !== res.locals.jwtData.id) {
			return res.status(401).send("Permissions did not match");
		}
		//@ts-ignore
		user.chats = [];
		await user.save();
		return res.status(200).json({ message: "OK" });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};
```

