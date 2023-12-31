---
tags:
  - AI-ChatBot
  - react
  - FrontEnd
---
# Building the React Front end for OpenAI ChatGPT

```jsx
// pages - Chat.tsx
import { Box, Avatar, Typography, Button, IconButton } from "@mui/material";
import { red } from "@mui/material/colors";
import React from "react";
import { useAuth } from "../contexts/AuthContext";
import ChatItem from "../components/chat/ChatItem";

import { IoMdSend } from "react-icons/io";

const chatMessages = [
	{
		role: "user",
		content: "Hello, can you tell me the weather forcast for tomorrow?",
	},
	{
		role: "assistant",
		content: "Sure! I can help with that. Please provide me with your location.",
	},
	{
		role: "user",
		content: "I'm based in Nottingham!",
	},
	{
		role: "assistant",
		content: "Great! Give me a moment to fetch the weather information for Nottingham.",
	},
	{
		role: "assistant",
		content: "The weather forecast for Nottingham is sunny with a high of 14 degrees and a low of 5 degrees. There is a 50% chance of rain, with 10% chance of snow.",
	},
	{
		role: "user",
		content: "That sounds perfect for December! Thanks for the information.",
	},
	{
		role: "assistant",
		content: "You're welcome! If you have any further questions, please feel free to ask.",
	},
];

const Chat = () => {
	const auth = useAuth();
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
				<Typography sx={{ textAlign: "center", fontSize: "40px", color: "white", mb: 2, mx: "auto", fontWeight: 600 }}>Model GPT3.5-turbo</Typography>
				<Box sx={{ width: "100%", height: "60vh", borderRadius: 3, mx: "auto", display: "flex", flexDirection: "column", overflow: "scroll", overflowX: "hidden", overflowY: "hidden", scrollBehavior: "smooth" }}>
					{chatMessages.map((chat, index) => (
						<ChatItem content={chat.content} role={chat.role} key={index} />
					))}
				</Box>
				<div style={{ width: "100%", padding: "20px", borderRadius: 8, backgroundColor: "rgb(17,27,39)", display: "flex", margin: "auto" }}>
					<input type="text" style={{ width: "100%", backgroundColor: "transparent", padding: "10px", border: "none", outline: "none", color: "white", fontSize: "20px" }}></input>
					<IconButton sx={{ ml: "auto", color: "white" }}>{<IoMdSend />}</IconButton>
				</div>
			</Box>
		</Box>
	);
};

export default Chat;

```
```jsx
// components - chat - ChatItem.tsx
import React from "React";
import { Box, Typography, Avatar } from "@mui/material";
import { useAuth } from "../../contexts/AuthContext";

const ChatItem = ({ content, role }: { content: string; role: "user" | "assistant" }) => {
	const auth = useAuth();
	return role === "assistant" ? (
		<Box sx={{ display: "flex", p: 2, bgcolor: "#004d5612", my: 2, gap: 2 }}>
			<Avatar sx={{ ml: "0" }}>
				<img src="openai.png" alt="openai" width={"30px"} />
			</Avatar>
			<Box>
				<Typography fontSize={"20px"}>{content}</Typography>
			</Box>
		</Box>
	) : (
		<Box sx={{ display: "flex", p: 2, bgcolor: "#004d56", gap: 2 }}>
			<Avatar sx={{ ml: "0", bgcolor: "black", color: "white" }}>{auth?.user?.name[0]}</Avatar>
			<Box>
				<Typography fontSize={"20px"}>{content}</Typography>
			</Box>
		</Box>
	);
};

export default ChatItem;

```

![[Pasted image 20231231172633.png]]

