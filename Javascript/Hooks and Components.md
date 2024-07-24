## 1 Components
- Components are the foundations of a React UI
- They are created, updated and destroyed
- Component updates are based on application state
- Rendering is costly so we only want it to happen when it needs to happen

## 2 Component Purity
- Component render functions in React are meant to be as closely as possibly, **functionally pure**. This means that they do not have **state** and they do not have **side effects**
- **State** is when the function remembers something, like the amount of times it has been called or what it was called with previously. The **only** thing a pure function knows is the arguments passed to it
- **Side effects** are where invoking the function causes something to happen. The only output a pure function has is what it returns 

## 3 Hook
Hooks are functions that let you hook into React state and lifecycle features from function components. **Hooks** don't work inside classes, they let you use React without classes. 
They are also the means by which a component can get around purity requirements. As such, their use is carefully controlled and there are rules that need to be followed: [here](https://reactjs.org/docs/hooks-rules.html)

This is seen in:
- `useState()` - provides a safe exception to the 'no state' requirement
- `useContext()` - provides a way of getting outside information other than through props
- `useEffect()` - provides a way to get around the 'no side effects' requirement [link to documentation](https://beta.reactjs.org/reference/react/useEffect)
	- It does break the React model and thus it needs care to use. Often it is better to extract the logic into a custom hook, which will allow you to add more optimisations later
	- It is also used to immediately initialise state when a component is constructed

### 3.1 UseEffect()

#### 3.1.1 useEffect(function, dependencyList) 
- allows the function to be executed when the component is rendered and the dependency list has changed. This allows for an updated state without waiting for user action
- Most of the time this is what you want to use
- Dependency list is often filled with **state variables** and/or **props**
- If a variable is in the dependency list and the effect function does not use that variable in some way, including it will call the function more than what is necessary

#### 3.1.2 useEffect(function)
-  If useEffect is called without a dependency list, the function will be call each time the component is rendered. **This is the most dangerous form of useEffect, should be limited to components that are not re rendered often or which are very lightweight. NEVER use to call fetch**

#### 3.1.3 useEffect(function, [])
- If it is called with an empty dependency list it will only be rendered the first time it is called **This is the safest form, only called on component construction**
		- Could be used to fetch data to initialise a components state, IF the same data is going to be retrieved each time
		- If the component is linked with some object not controlled by React, it may be constructed here, in which case dont forget about cleanup function

#### 3.1.4 Cleanup
- useEffect() can optionally return a function itself
- If it does return one, it is used as a **cleanup** function by react. This will be called when the component is unmounted OR before the corresponding useEffect() is triggered again
- The cleanup function is used to undo anything persistent that the original useEffect established
- i.e. if you are using a non react controlled element to play music while your component is open, you would stop that music and clean up the element in the cleanup function
- Also used to close connections

#### 3.1.5 StrictMode
- StrictMode does many things in development mode to check the React apps validity
- One of these is that when the components are constructed, they are initially mounted, then unmounted then mounted again
	- this is to ensure that your useEffect logic is implemented correctly
- This means that useEffect() is run twice on component construction while in development mode
- In this case the cleanup function can be used to abort an in progress fetch() call if the component is unmounted before it can complete, which will result in fewer calls to external API while testing


Popular hooks include: 
- `useState()`
- `useEffect()`
	- `useEffect()` allows updates after a render has occurred. Think of it as being `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined

[Don't call hooks from anywhere but a react component]
### 3.2 useEffect()
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

### 3.3 Function based useState()
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

### 3.4 Class based useState()
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

## 1 Mounting a component
- Component is created using a constructor or component
- Set initial state when it is first created
- Component is then mounted, either directly, usually for a high level or root component, or as a rendering within a more complex component. 

`componentDidMount` is invoked as soon as the component is mounted. This is used for complex setup, such as fetching data from network. It is also a **partner method** used to clean things up as the component is removed

## 2 Update Sequence
An update can be caused by changes to props or state. these methods are called in the following order when a component is being re-rendered:

- `static getDerivedStateFromProps()`
- `shouldComponentUpdate()`
- `render()`
- `getSnapshotBeforeUpdate()`
- `componentDidUpdate()`

## 3 Unmounting
Called when a component needs to be removed from the DOM:
- `componentWillUnmount()`

# Component Libraries
### 0.1 reactstrap
- 