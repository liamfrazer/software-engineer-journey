---
tags:
  - AI-ChatBot
  - react
  - form-data
  - axios
---
# Login Page and handling form data
```jsx
import React from "react";
import { Box, Typography, Button } from "@mui/material";
import CustomisedInput from "../components/shared/CustomisedInput";
import { IoIosLogIn } from "react-icons/io";

const Login = () => {
	return (
		<Box width={"100%"} height={"100%"} display="flex" flex={1}>
			<Box
				padding={8}
				mt={8}
				display={{ xs: "none", sm: "none", md: "flex" }}
			>
				<img
					src="airobot.png"
					alt="Robot"
					style={{ width: "400px" }}
				></img>
			</Box>
			<Box
				display={"flex"}
				flex={{ xs: 1, sm: 1, md: 0.5 }}
				justifyContent={"center"}
				alignItems={"center"}
				padding={2}
				ml={"auto"}
				mt={16}
			>
				<form
					style={{
						margin: "auto",
						padding: "30px",
						boxShadow: " 10px 10px 20px #000",
						borderRadius: "10px",
						border: "none",
					}}
				>
					<Box
						sx={{
							display: "flex",
							flexDirection: "column",
							justifyContent: "center",
						}}
					>
						<Typography
							variant="h4"
							textAlign="center"
							padding={2}
							fontWeight={600}
						>
							Login
						</Typography>
						<CustomisedInput
							type={"email"}
							label={"Email"}
							name={"email"}
						/>
						<CustomisedInput
							type={"password"}
							label={"Password"}
							name={"password"}
						/>
						<Button
							type="submit"
							sx={{
								px: 2,
								py: 1,
								mt: 2,
								width: "400px",
								borderRadius: 2,
								bgcolor: "#00fffc",
								":hover": { bgcolor: "white", color: "black" },
							}}
							endIcon={<IoIosLogIn />}
						>
							Login
						</Button>
					</Box>
				</form>
			</Box>
		</Box>
	);
};

export default Login;

```
![[Pasted image 20231231115730.png]]

* We can create a function to grab the form data without having to use a state

```jsx
<form onSubmit={(e) => handleSubmit(e)} style={{ margin: "auto", padding: "30px", boxShadow: " 10px 10px 20px #000", borderRadius: "10px", border: "none" }}>

```
```jsx
	const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
		e.preventDefault();
		const formData = new FormData(e.currentTarget);
		const email = formData.get("email");
		const password = formData.get("password");
		console.log(email, password);
	};
```
```console
liam.frazer@gmail.com 12345
```
