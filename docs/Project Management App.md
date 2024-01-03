---
tags:
  - react
  - project
---
# Project Management App

1. Add a Projects Sidebar Component
```jsx
// app.jsx
import ProjectsSidebar from "./components/ProjectsSidebar";

function App() {
	return (
		<main>
			<ProjectsSidebar />
		</main>
	);
}

export default App;
```
```jsx
// ProjectSidebar.jsx
const ProjectsSidebar = () => {
	return (
		<aside>
			<h2>Your Projects</h2>
			<div>
				<button>+ Add Project</button>
			</div>
			<ul></ul>
		</aside>
	);
};

export default ProjectsSidebar;

```

2. Styling the sidebar & button with Tailwind CSS
3. 