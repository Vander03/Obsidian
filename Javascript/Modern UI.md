
## Common ideas
- Isolate application logic from presentation
- Limit the role of the ROM on ordinary processing
- Employ a virtual DOM for *much* master updates
	- Only in React and Angular
- Decouple the client and server components
- Declarative templating on the client side
## Differences
### Frameworks
- A framework imposes an application structure
- Has strong opinions about data flows
- Offers a coherent suite of services
- Manages the upgrade path and integration for you
- Angular is a framework

### Libraries
- A subset of the functionality needed for a full application
- Need to play nicely with other services
- Need to manage interactions with other services yourself
- React tis a templating library
- Vue can be a view library or a full framework

## Model-View-Controller
![300](Pasted%20image%2020240308191138.png)

### Data Binding
- One way binding
	- Changes to the model reflected in the view
	- But changes in the view do not propagate to the model
	- This is the approach taken by React
- Two way binding
	- Changes to the mode are reflected in the view
	- Changes in the view do propagate to the model
	- This is the approach taken by Angular and supported in Vue

## Vue
Fast virtual Dom.
Relies on its virtual Dom to propagate updates to the real Dom whenever necessary


## Angular
Based around **components**, which define a **view**. **Views** are a set of screen elements that Angular can choose among and modify according to your program logic and data.
**Components** use services, which provide specific functionality not directly related to **views**. Service providers can be *injected* into component *dependencies* making code modular, reusable and efficient.

**Angular** provides its own module specification for organising the application


## React
 - JS library for views
 - Developed by Facebook
 - Templating library like Pug
 - Uses JSX (Javascript Extension) for syntax
 - One way data binding
 - Does not have a standard routing library
 - Not a full MVC framework like Angular

### JSX
Javascript Extension templating

```jsx
function formatName(user) {
	return user.firstName + ' ' + user.lastName;
}
const user = { // object
	firstName: 'Harper',
	lastName: 'Perez'
};
const element = (
	<h1>
	Hello, {formatName(user)}!
	</h1>
);
ReactDOM.render( // embedded within a call to the ReactDOM.render
	element, 
	document.getElementById('root') // this attaches element to document
);
```

### Anchor on page
**React** attaches to a point on the webpage by connecting with an HTML class (normally designated "root"), by assigning `const rootElement = document.getElementById("root)`;
and placing this in the `ReactDOM.render()` function shown above, normally present in `index.js`. 

### Index
`ReactDOM` will update changes as they're needed 

```jsx
import ( StrictMode ) from "react";
import ReactDOM from "react-dom";

import App from "./App"; // import function here

const rootElement = document.getElementById("root");
ReactDOM.render (
	<StrictMode>
		<App />
	</StrictMode>
	rootElement
);
```

### App 
`App.js` is where the application code is kept

```jsx
import ./"styles.css";

function formatName(user) {
	return user.firstName + ' ' + user.lastName;
}

const user = {
	firstName: 'Harper'.
	lastName: 'Prerez'
};

export default function App() { // makes this function available in the other file
	return (
		<div className="App">
			<h1>Hellp, {formatName(user)}!</h1>
		</div>
	);
}
```


## Rendering and Updates

```jsx
function tick() {
const element = (
<div>
	<h1>Hello, world!</h1>
	<h2>It is {new Date().toLocaleTimeString()}.</h2>
</div>
);
ReactDOM.render(element, document.getElementById('root'));
}
setInterval(tick, 1000);
```

## Props
Props are passed to the component as a single object
Access each field as a property, with unused fields being ignored
```jsx
import React from "react";
import ReactDOM from "react-dom";

import "./styles.css";

const Lucy = {
	name: "Lucy",
	age: 8, 
	bark: "very loud"
}

// modified using fields from object Lucy
// ...Lucy is shorthand for grabbing all the elements from the object to expand and match it 1x1 with the new one
function App() {
	return (
		<div className="App">
			<h1>Golden Dogs</h1>
			<Golden {...Lucy} /> 
			<Golden name="Sam" age="15" bark="non-existent" />
		</div>
	);
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

// original with fields passed from render
function App(props) {
	return (
		<div className="App">
			<h1>Hello Simple Component</h1>
			<h2>Name is: {props.name} </h2>
			<h2>Age is: {props.age} </h2>
		</div>
	);
}



const rootElement = document.getElementById("root");
ReactDOM.render(<App name="Lucy" age="8" />, rootElement); // passes info to props

```

 