---
tags:
  - MongoDB
  - Mongoose
---
# Integrate MongoDB Database Connection
![[Pasted image 20231230111022.png]]
```jsx
import { config } from "dotenv";
config();
```
![[Pasted image 20231230111336.png]]
```jsx
import { connect, disconnect } from "mongoose";
const connectToDatabase = async () => {
	try {
		await connect(process.env.MONGODB_URI as string);
	} catch (error) {
		console.error(error);
		throw new Error("Failed to connect to MongoDB");
	}
};

const disconnectFromDatabase = async () => {
	try {
		await disconnect();
	} catch (error) {
		console.error(error);
		throw new Error("Failed to disconnect from MongoDB");
	}
};

export { connectToDatabase, disconnectFromDatabase };

```


