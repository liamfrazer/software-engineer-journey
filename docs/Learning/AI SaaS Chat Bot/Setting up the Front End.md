---
tags:
  - react
  - "#AI-ChatBot"
---
# Setting up the Front End

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.tsx";
import "./index.css";
import { createTheme, ThemeProvider } from "@mui/material";
import { BrowserRouter } from "react-router-dom";

const theme = createTheme({
	typography: {
		fontFamily: "Roboto Slab, serif",
		allVariants: { color: "white" },
	},
});

ReactDOM.createRoot(document.getElementById("root")!).render(
	<React.StrictMode>
		<BrowserRouter>
			<ThemeProvider theme={theme}>
				<App />
			</ThemeProvider>
		</BrowserRouter>
	</React.StrictMode>
);

```

```console
npm install @mui/material @emotion/react @emotion/styled react-icons react-router-dom react-hot-toast
```

## Routing

```jsx
import Header from "./components/Header";
import { Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import Login from "./pages/Login";
import Signup from "./pages/Signup";
import Chat from "./pages/Chat";
import NotFound from "./pages/NotFound";

function App() {
	return (
		<main>
			<Header />
			<Routes>
				<Route path="/" element={<Home />} />
				<Route path="/login" element={<Login />} />
				<Route path="/signup" element={<Signup />} />
				<Route path="/chat" element={<Chat />} />
				<Route path="*" element={<NotFound />} />
			</Routes>
		</main>
	);
}

export default App;
```

### Logo with Material UI Styling

```jsx
import React from "react";
import { Link } from "react-router-dom";
import { Typography } from "@mui/material";

const Logo = () => {
	return (
		<div
			style={{
				display: "flex",
				marginRight: "auto",
				alignItems: "center",
				gap: "15px",
			}}
		>
			<Link to={"/"}>
				<img
					src="openai.png"
					alt="openai"
					width={"30px"}
					height={"30px"}
					className="image-inverted"
				/>
			</Link>
			<Typography
				sx={{
					display: { md: "block", sm: "none", xs: "none" },
					marginRight: "auto",
					fontWeight: "800",
					textShadow: "2px 2px 20px #000",
				}}
			>
				<span style={{ fontSize: "20px" }}>MERN</span>-GPT
			</Typography>
		</div>
	);
};

export default Logo;

```

## Header 

```jsx
import React from "react";
import { AppBar, Toolbar } from "@mui/material";
import Logo from "./shared/Logo";

const Header = () => {
	return (
		<AppBar
			sx={{
				bgcolor: "transparent",
				boxShadow: "none",
				position: "static",
			}}
		>
			<Toolbar sx={{ display: "flex" }}>
				<Logo />
			</Toolbar>
		</AppBar>
	);
};

export default Header;

```

* The context API will be very useful to show components to the user, depending on whether they're logged in or not using our backend.

## Component showing based on context
```jsx
import { createContext } from "react";
import { useState, ReactNode, useEffect, useContext } from "react";

type User = {
	name: string;
	email: string;
};
type UserAuth = {
	isLoggedIn: boolean;
	user: User | null;
	login: (email: string, password: string) => Promise<void>;
	signup: (name: string, email: string, password: string) => Promise<void>;
	logout: () => Promise<void>;
};
const AuthContext = createContext<UserAuth | null>(null);
const AuthProvider = ({ children }: { children: ReactNode }) => {
	const [user, setUser] = useState<User | null>(null);
	const [isLoggedIn, setIsLoggedIn] = useState<boolean>(false);

	useEffect(() => {
		// Fetch if the user's cookies are valid then skip login
	}, []);
	const login = async (email: string, password: string) => {};
	const signup = async (name: string, email: string, password: string) => {};
	const logout = async () => {};

	const value = {
		user,
		isLoggedIn,
		login,
		logout,
		signup,
	};
	return (
		<AuthContext.Provider value={value}>{children}</AuthContext.Provider>
	);
};

const useAuth = () => useContext(AuthContext);

export { useAuth, AuthProvider };

```

* We can use an overall application state within the AuthContext.tsx file

```jsx
import React from "react";
import { AppBar, Toolbar } from "@mui/material";
import Logo from "./shared/Logo";

import { useAuth } from "../contexts/AuthContext";
import NavigationLink from "./shared/NavigationLink";

const Header = () => {
	const auth = useAuth();
	return (
		<AppBar
			sx={{
				bgcolor: "transparent",
				boxShadow: "none",
				position: "static",
			}}
		>
			<Toolbar sx={{ display: "flex" }}>
				<Logo />
				<div>
					{auth?.isLoggedIn ? (
						<>
							<NavigationLink
								bg="#00fffc"
								to="/chat"
								text="Go to Chat"
								textColor="black"
							/>
							<NavigationLink
								bg="#51539f"
								to="/"
								text="Logout"
								textColor="white"
								onClick={auth.logout}
							/>
						</>
					) : (
						<>
							<NavigationLink
								bg="#00fffc"
								to="/login"
								text="Login"
								textColor="black"
							/>
							<NavigationLink
								bg="#51539f"
								to="/signup"
								text="Signup"
								textColor="white"
							/>
						</>
					)}
				</div>
			</Toolbar>
		</AppBar>
	);
};

export default Header;

```

