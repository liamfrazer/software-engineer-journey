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

