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
```jsx
// App.jsx
        <main className="h-screen my-8">
```
```jsx
//ProjectSidebar.jsx
		<aside className="w-1/3 px-8 py-16 bg-stone-900 text-stone-50 md:w-72 rounded-r-xl">
		
			<h2 className="mb-8 font-bold uppercase md:text-xl text-stone-200">Your Projects</h2>
			
                <button className="px-4 py-2 text-xs md:text-base rounded-md bg-stone-700 text-stone-400 hover:bg-stone-600 hover:text-stone-100">+ Add Project</button>
                
```

3. Adding the "New Project" Component & A Reusable Input Component
```jsx
// Input.jsx
const Input = ({ label, textArea, ...props }) => {
	return (
		<p>
			<label>{label}</label>
			{textArea ? <textarea {...props} /> : <input {...props} />}
		</p>
	);
};

export default Input;

```
```jsx
// NewProject.jsx
import Input from "./Input";

const NewProject = () => {
	return (
		<div>
			<menu>
				<li>
					<button>Cancel</button>
				</li>
				<li>
					<button>Save</button>
				</li>
			</menu>
			<div>
				<Input label="Title" />
				<Input label="Description" textArea />
				<Input label="Due Date" />
			</div>
		</div>
	);
};

export default NewProject;

```
4. Styling Buttons & Inputs with Tailwind CSS
5. 
