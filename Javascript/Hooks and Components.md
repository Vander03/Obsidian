## Components
- Components are the foundations of a React UI
- They are created, updated and destroyed
- Component updates are based on application state
- Rendering is costly so we only want it to happen when it needs to happen


## Hook
Hooks are functions that let you hook into React state and lifecycle features from function components. **Hooks** don't work inside classes, they let you use React without classes. 

Popular hooks include: 
- `useState()`
- `useEffect()`
	- `useEffect()` allows updates after a render has occurred. Think of it as being `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined

[Don't call hooks from anywhere but a react component]
### useEffect()
```JSX
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

### Function based useState()
```JSX
import React, {useState} from 'react';

function Example() {
	// Declare a new state varm called 'count'
	// here: 
	// count - storage var
	// setCount - update function
	// useState - hook function
	const [count, setCount] = useState(0);

	return (
		<div>
			<p>You clicked {count} times</p>
			// here setCount updates count via the previously set up hook
			<button onClick={() => setCount(count + 1)}>
			Click me
			</button>
		</div>
	);
}
```

### Class based useState()
```JSX
class Example extends React-Component {
	constructor(props) {
		super(props);
		this.state = {
			count: 0
		};
	}

	render() {
		return(
			<div>
				<p>You clicked (this.state.count) times</p>
				// updates this count by reassigning it its value + 1, using setState hook
				<button onClick={() => this.setState({count: this.state.count + 1})}
			</div>
		);
	}
}
```


# React Lifecycle 

![700](Pasted%20image%2020240313200452.png)

## Mounting a component
- Component is created using a constructor or component
- Set initial state when it is first created
- Component is then mounted, either directly, usually for a high level or root component, or as a rendering within a more complex component. 

`componentDidMount` is invoked as soon as the component is mounted. This is used for complex setup, such as fetching data from network. It is also a **partner method** used to clean things up as the component is removed

## Update Sequence
An update can be caused by changes to props or state. these methods are called in the following order when a component is being re-rendered:

- `static getDerivedStateFromProps()`
- `shouldComponentUpdate()`
- `render()`
- `getSnapshotBeforeUpdate()`
- `componentDidUpdate()`

## Unmounting
Called when a component needs to be removed from the DOM:
- `componentWillUnmount()`


