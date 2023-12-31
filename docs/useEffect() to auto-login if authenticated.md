---
tags:
  - AI-ChatBot
  - authenticated
  - useEffect
---
# useEffect() to auto-login if authenticated

```jsx
// Routes - user.routes.ts
userRoutes.get("/auth-status", verifyToken, verifyUser);
```
```jsx
// utils - token-manager.ts
const verifyToken = async (req: Request, res: Response, next: NextFunction) => {
	const token = req.signedCookies[`${COOKIE_NAME}`];
	if (!token || token.trim() === "") {
		return res.status(401).json({ message: "Token not received" });
	}
	return new Promise<void>((resolve, reject) => {
		return jwt.verify(token, process.env.JWT_SECRET, (err, success) => {
			if (err) {
				reject(err.message);
				return res.status(401).json({ message: "Token expired" });
			} else {
				console.log("Token Verification Successful");
				resolve();
				res.locals.jwtData = success;
				return next();
			}
		});
	});
};
```
```jsx
// helpers - api-communicator.ts
const checkAuthStatus = async () => {
	const res = await axios.get("/user/auth-status");
	if (res.status !== 200) {
		throw new Error(`Unable to Authenticate`);
	}
	const data = await res.data;
	return data;
};
```
```jsx
// contexts - AuthContexts.tsx
const AuthProvider = ({ children }: { children: ReactNode }) => {
	const [user, setUser] = useState<User | null>(null);
	const [isLoggedIn, setIsLoggedIn] = useState<boolean>(false);

	useEffect(() => {
		// Fetch if the user's cookies are valid then skip login
		async function checkStatus() {
			const data = await checkAuthStatus();
			if (data) {
				setUser({ email: data.email, name: data.name });
				setIsLoggedIn(true);
			}
		}
		checkStatus();
	}, []);
	const login = async (email: string, password: string) => {
		const data = await loginUser(email, password);
		if (data) {
			setUser({ email: data.email, name: data.name });
			setIsLoggedIn(true);
		}
	};
```
```jsx
// controllers - user-controller.ts
const verifyUser = async (req: Request, res: Response, next: NextFunction) => {
	try {
		const user = await User.findById(res.locals.jwtData.id);
		if (!user) {
			return res.status(401).send("User not found or Token malfunctioned");
		}
		if (user._id.toString() !== res.locals.jwtData.id) {
			return res.status(401).send("Permissions did not match");
		}

		return res.status(200).json({ message: "OK", name: user.name, email: user.email });
	} catch (error) {
		console.log(error);
		return res.status(200).json({ message: "ERROR", cause: error.message });
	}
};
```


