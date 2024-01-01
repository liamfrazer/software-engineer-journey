---
tags:
  - AI-ChatBot
  - routes
  - Protected
  - useNavigate
---
# Enabling Protected Routes within the Front End
```jsx
// pages - Chat.tsx
	useEffect(() => {
		if (!auth?.user) {
			return navigate("/login");
		}
	}, [auth, navigate]);
```
```jsx
// routes - user.routes.ts
userRoutes.get("/logout", verifyToken, logoutUser);
```
```jsx
// helpers - api-communicator.ts
const userLogout = async () => {
	const res = await axios.get("/user/logout");
	if (res.status !== 200) {
		console.log(res.data);
		throw new Error(`Unable to delete chat`);
	}
	const data = await res.data;
	return data;
};
```
```jsx
// contexts - AuthContext.tsx
	const logout = async () => {
		await userLogout();
		setIsLoggedIn(false);
		setUser(null);
		window.location.reload();
	};
```
```jsx
// controllers - user-controllers.ts
const logoutUser = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const user = await User.findById(res.locals.jwtData.id);
		if (!user) {
			return res.status(401).send("User not found or Token malfunctioned");
		}
		if (user._id.toString() !== res.locals.jwtData.id) {
			return res.status(401).send("Permissions did not match");
		}

		res.clearCookie(COOKIE_NAME, {
			httpOnly: true,
			domain: "localhost",
			signed: true,
			path: "/",
		});

		return res.status(200).json({ message: "OK", name: user.name, email: user.email });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};
```


