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
```jsx
// Input.jsx
const Input = ({ label, textArea, ...props }) => {
	const classes = "w-full p-1 border-b-2 rounded-sm border-stone-300 bg-stone-200 text-stone-600 focus:outline-none focus:border-stone-600";
	return (
		<p className="flex flex-col gap-1 my-4">
			<label className="text-sm font-bold uppercase text-stone-500">{label}</label>
			{textArea ? <textarea className={classes} {...props} /> : <input className={classes} {...props} />}
		</p>
	);
};

export default Input;

```
5. Splitting Components to Split JSX & Tailwind Styles (for Higher Reusability)
```jsx
// NoProjectSelected.jsx
import noProjectImage from "../assets/no-projects.png";
import Button from "./Button";
const NoProjectSelected = () => {
	return (
		<div className="mt-24 text-center w-2/3">
			<img src={noProjectImage} alt="An empty task list" className="w-16 h-16 object-contain mx-auto" />
			<h2 className="text-xl font-bold text-stone-500 my-4">No Project Selected</h2>
			<p className="text-stone-400 mb-4">Select a project or start a new one</p>
			<p className="mt-8">
				<Button>Create New Project</Button>
			</p>
		</div>
	);
};

export default NoProjectSelected;

```
```jsx
// Button.jsx
const Button = ({ children, ...props }) => {
	return (
		<button className="px-4 py-2 text-xs md:text-base rounded-md bg-stone-700 text-stone-400 hover:bg-stone-600 hover:text-stone-100" {...props}>
			{children}
		</button>
	);
};

export default Button;

```
```jsx
// App.jsx
import NewProject from "./components/NewProject";
import NoProjectSelected from "./components/NoProjectSelected";
import ProjectsSidebar from "./components/ProjectsSidebar";

function App() {
	return (
		<main className="h-screen my-8 flex gap-8">
			<ProjectsSidebar />
			{/* <NewProject /> */}
			<NoProjectSelected />
		</main>
	);
}

export default App;

```
```jsx
//ProjectsSidebar.jsx
import Button from "./Button";

const ProjectsSidebar = () => {
	return (
		<aside className="w-1/3 px-8 py-16 bg-stone-900 text-stone-50 md:w-72 rounded-r-xl">
			<h2 className="mb-8 font-bold uppercase md:text-xl text-stone-200">Your Projects</h2>
			<div>
				<Button>+ Add Project</Button>
			</div>
			<ul></ul>
		</aside>
	);
};

export default ProjectsSidebar;

```

6.  Managing State to Switch Between Components
