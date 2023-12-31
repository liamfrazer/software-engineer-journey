---
tags:
  - AI-ChatBot
  - react
  - Express
  - axios
---
# Axios - Sending the API Request from React to Express

* Axios can be used to send the request from the React frontend to the Express backend

```jsx
import axios from "axios";
axios.defaults.baseURL = "http://localhost:5000/api/v1";
axios.defaults.withCredentials = true;
```

```jsx
// Helper - api-communicator.ts

import axios from "axios";

const loginUser = async (email: string, password: string) => {
	const res = await axios.post("/user/login", { email, password });
	if (res.status !== 200) {
		throw new Error(`Unable to Login: ${res.data.message}`);
	}
	const data = await res.data;
	return data;
};

export { loginUser };

```

```jsx
// Contexts - AuthContext.tsx
import { loginUser } from "../helpers/api-communicator";

	const login = async (email: string, password: string) => {
		const data = await loginUser(email, password);
		if (data) {
			setUser({ email: data.email, name: data.name });
			setIsLoggedIn(true);
		}
	};
```

```jsx
// Pages - Login.tsx
const Login = () => {
	const auth = useAuth();
	const handleSubmit = async (e: React.FormEvent<HTMLFormElement>) => {
		e.preventDefault();
		const formData = new FormData(e.currentTarget);
		const email = formData.get("email") as string;
		const password = formData.get("password") as string;
		try {
			toast.loading("Signing In!", { id: "login" });
			await auth?.login(email, password);
			toast.success("Signed In Successfully", { id: "login" });
		} catch (error) {
			console.log(error);
			toast.error("Signing In Failed", { id: "login" });
		}
	};
```

![[Pasted image 20231231124322.png]]
```console
[1] POST /api/v1/user/login 200 73.555 ms - 61
```




