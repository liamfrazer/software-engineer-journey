---
tags:
  - AI-ChatBot
  - authenticated
  - useEffect
---
# useEffect() to auto-login if authenticated

```jsx
// Routes - user.routes.ts
userRoutes.get("/auth-status", verifyToken);
```
```jsx
// utils - token-manager.ts
const verifyToken = async (req: Request, res: Response, next: NextFunction) => {
	const token = req.signedCookies[`${COOKIE_NAME}`];
	console.log(token);
};
```
```jsx
// helpers - api-communicator.ts
const checkAuthStatus = async () => {
	const res = await axios.post("/user/auth-status");
	if (res.status !== 200) {
		throw new Error(`Unable to Authenticate: ${res.data.message}`);
	}
	const data = await res.data;
	return data;
};
```

