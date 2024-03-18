## Simple function based component

```JSX
function Name(props) {
	return(
	<h1> Name is {props.name}</h1>
	)
}
```

## Function based approach
```JSX
import React from "react";
import ReactDOM from "react-dom";

import "./styles.css";

function App() {
	return (
		<div className="App">
			<h1>Hello CodeSandbox</h1>
			<h2>Start editing to see some magic happen!</h2>
		</div>
	);
}

const rootElement = document.getElementByID("root");
ReactDOM.render(<App />, rootElement);
```

## Class based approach
```JSX
import React from "react";
import ReactDOM from "react-dom";

import "./styles.css";

class App extends React.Component {
	render () { // this render keyword is the key difference between class based and function based
		return (
			<div className="App">
				<h1>Hello CodeSandbox</h1>
				<h2>Start editing to see some magic happen!</h2>
			</div>		
		);
	}
}
const rootElement = document.getElementByID("root");
ReactDOM.render(<App />, rootElement);
```

## Example: Website in Class based and Function based

### Function based
```JSX
// Function based
import "./styles.css"

function Golden(props) {
	return (
		<div className="Golden">
			<h2>Name is: {prop.name}</h2>
			<h2>Age is: {prop.age}</h2>
			<h2>Bark is: {prop.bark}</h2>
		</div>
	);
}

const Lucy = {
	name: "Lucy",
	age: 8,
	bark: "very loud"
}

function App() {
	return(
		// class App entry point
		<div className="App"> 
			<h1>Golden Dogs</h1>
			<Golden {...Lucy} />
			// this is how to pass params to a function
			<Golden name="Sam" age="15" bark="non-existent" />
		</div>
	);
}
const rootElement = document.getElementByID("root");
ReactDOM.render(<App />, rootElement);
```

### Class based
```JSX

// Main App class
const Lucy = {
	name: "Lucy",
	age: 8,
	bark: "very loud"
}

class App extends React.Component {
	constructor(props) {
		super(props);
	}
	render() {
		return (
			<div className="App">
				<h1>Golden Dogs</h1>
				<Golden {...Lucy} />
				<Golden name="Sam" age="15" bark="non-existent" />
			</div>		
		);
	}
}
const rootElement = document.getElementByID("root");
ReactDOM.render(<App />, rootElement);

-------------------------
// Golden Class
import React from "react";
import ReactDOM from "react-dom";

import "./styles.css"

class Golden extends React.Component {
	constructor(props) {
		super(props);
		this.state = {...props};
	}

	render() {
		return(
			<div className="Golden">
				<h2>Name is: {this.state.name}</h2>
				<h2>Age is: {this.state.age}</h2>
				<h2>Bark is: {this.state.bark}</h2>
			</div>
		);
	}
}
```

**Important note to update state:** use `setState()` to update field
e.g.
```JSX
// init control bark display
this.state.displayBark = false;

// update
this.setState({displayBark: true});
```