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


