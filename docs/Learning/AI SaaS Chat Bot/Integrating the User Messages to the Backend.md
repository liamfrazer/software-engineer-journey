---
tags:
  - AI-ChatBot
  - APIs
---
# Integrating the User Messages to the Backend
```jsx
// Chat - ChatItem.tsx
import { Box, Typography, Avatar } from "@mui/material";
import { useAuth } from "../../contexts/AuthContext";

import { Prism as SyntaxHighlighter } from "react-syntax-highlighter";
import { coldarkDark } from "react-syntax-highlighter/dist/esm/styles/prism";

const extractCodeFromString = (message: string) => {
	if (message.includes("```")) {
		const blocks = message.split("```");
		return blocks;
	}
};

const isCodeBlock = (str: string) => {
	if (str.includes("=") || str.includes(";") || str.includes("[") || str.includes("]") || str.includes("{") || str.includes("}") || str.includes("#") || str.includes("//")) {
		return true;
	}
	return false;
};

const ChatItem = ({ content, role }: { content: string; role: "user" | "assistant" }) => {
	const messageBlocks = extractCodeFromString(content);
	const auth = useAuth();
	return role === "assistant" ? (
		<Box sx={{ display: "flex", p: 2, bgcolor: "#004d5612", my: 2, gap: 2 }}>
			<Avatar sx={{ ml: "0" }}>
				<img src="openai.png" alt="openai" width={"30px"} />
			</Avatar>
			<Box>
				{!messageBlocks && <Typography sx={{ fontSize: "20px" }}>{content}</Typography>}
				{messageBlocks &&
					messageBlocks.length &&
					messageBlocks.map((block) =>
						isCodeBlock(block) ? (
							<SyntaxHighlighter style={coldarkDark} language="javascript">
								{block}
							</SyntaxHighlighter>
						) : (
							<Typography sx={{ fontSize: "20px" }}>{block}</Typography>
						)
					)}
			</Box>
		</Box>
	) : (
		<Box sx={{ display: "flex", p: 2, bgcolor: "#004d56", gap: 2, my: 2 }}>
			<Avatar sx={{ ml: "0", bgcolor: "black", color: "white" }}>{auth?.user?.name[0]}</Avatar>
			<Box>
				{!messageBlocks && <Typography sx={{ fontSize: "20px" }}>{content}</Typography>}
				{messageBlocks &&
					messageBlocks.length &&
					messageBlocks.map((block) =>
						isCodeBlock(block) ? (
							<SyntaxHighlighter style={coldarkDark} language="javascript">
								{block}
							</SyntaxHighlighter>
						) : (
							<Typography sx={{ fontSize: "20px" }}>{block}</Typography>
						)
					)}
			</Box>
		</Box>
	);
};

export default ChatItem;

```
```jsx
// Pages - Chat.tsx
import { Box, Avatar, Typography, Button, IconButton } from "@mui/material";
import { red } from "@mui/material/colors";
import { useAuth } from "../contexts/AuthContext";
import ChatItem from "../components/chat/ChatItem";
import { useRef, useState } from "react";
import { IoMdSend } from "react-icons/io";
import { sendChatRequest } from "../helpers/api-communicator";

type Message = {
	role: "user" | "assistant";
	content: string;
};

const Chat = () => {
	const inputRef = useRef<HTMLInputElement | null>(null);
	const auth = useAuth();
	const [chatMessages, setChatMessages] = useState<Message[]>([]);
	const handleSubmit = async () => {
		const content = inputRef.current?.value as string;
		if (inputRef && inputRef.current) {
			inputRef.current.value = "";
		}
		const newMessage: Message = { role: "user", content };
		setChatMessages((prev) => [...prev, newMessage]);
		const chatData = await sendChatRequest(content);
		setChatMessages([...chatData.chats]);
		// Send message to API
	};
	return (
		<Box sx={{ display: "flex", flex: 1, width: "100%", height: "100%", mt: 3, gap: 3 }}>
			<Box sx={{ display: { md: "flex", sm: "none", xs: "none" }, flex: 0.2, flexDirection: "column" }}>
				<Box sx={{ display: "flex", width: "100%", height: "60vh", bgcolor: "rgb(17,29,39)", borderRadius: 5, flexDirection: "column", mx: 3 }}>
					<Avatar sx={{ mx: "auto", my: 2, bgcolor: "white", color: "black", fontWeight: 700 }}>{auth?.user?.name[0]}</Avatar>
					<Typography sx={{ mx: "auto", fontFamily: "work sans" }}>You are talking to a ChatBOT</Typography>
					<Typography sx={{ mx: "auto", fontFamily: "work sans", my: 4, p: 3 }}>You can ask some questions related to Knowledge, Business, Advice, Education, etc. But please avoid sharing personal information.</Typography>
					<Button sx={{ width: "200px", my: "auto", color: "white", fontWeight: 700, borderRadius: 3, mx: "auto", bgcolor: red[300], ":hover": { bgcolor: red[400] } }}>Clear Conversation</Button>
				</Box>
			</Box>
			<Box sx={{ display: "flex", flex: { md: 0.8, sx: 1, sm: 1 }, flexDirection: "column", px: 3 }}>
				<Typography sx={{ textAlign: "center", fontSize: "40px", color: "white", mb: 2, mx: "auto", fontWeight: 600 }}>Model GPT 3.5-turbo</Typography>
				<Box sx={{ width: "100%", height: "60vh", borderRadius: 3, mx: "auto", display: "flex", flexDirection: "column", overflow: "scroll", overflowX: "hidden", overflowY: "auto", scrollBehavior: "smooth" }}>
					{chatMessages.map((chat, index) => (
						<ChatItem content={chat.content} role={chat.role} key={index} />
					))}
				</Box>
				<div style={{ width: "100%", padding: "20px", borderRadius: 8, backgroundColor: "rgb(17,27,39)", display: "flex", margin: "auto" }}>
					<input ref={inputRef} type="text" style={{ width: "100%", backgroundColor: "transparent", padding: "10px", border: "none", outline: "none", color: "white", fontSize: "20px" }}></input>
					<IconButton onClick={handleSubmit} sx={{ ml: "auto", color: "white" }}>
						{<IoMdSend />}
					</IconButton>
				</div>
			</Box>
		</Box>
	);
};

export default Chat;

```
```jsx
// helpers - api-communicator.ts
import axios from "axios";

const loginUser = async (email: string, password: string) => {
	const res = await axios.post("/user/login", { email, password });
	if (res.status !== 200) {
		throw new Error(`Unable to Login`);
	}
	const data = await res.data;
	return data;
};

const checkAuthStatus = async () => {
	const res = await axios.get("/user/auth-status");
	if (res.status !== 200) {
		throw new Error(`Unable to Authenticate`);
	}
	const data = await res.data;
	return data;
};

const sendChatRequest = async (message: string) => {
	const res = await axios.post("/chat/new", { message });
	if (res.status !== 200) {
		console.log(res.data);
		throw new Error(`Unable to send chat`);
	}
	const data = await res.data;
	return data;
};

export { loginUser, checkAuthStatus, sendChatRequest };

```

