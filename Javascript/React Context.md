## 1 Application State
- Complex application involve numerous components
- Components share state with child components
	- But not with siblings or parents
	- We make a lot of use of `props`

- Application state may be handled in a number of ways
	- Component trees - move the state upwards and use props
		- If we have components that need to share state, we move the state upwards until we get to a component that is a parent to both of those components, then use properties to make sure both of them can handle it
	- Redux - the old standard **not covered**
	- Context - the new

In application state, we always want to use the simplest approach that works
- In many cases, just components and useState are sufficient. There is no need to overcomplicate
- Maybe your application is so complex and nested that you would need to pass props through many components, **called prop-drilling**. For this use case, `useContext` is your friend


## 2 Component hierarchies
- Ideas similar to OOP
- Abstract away common state from child components
- Hold this state somewhere up the component tree to be easily accessible to children
- We pass the state information down via props
## 3 Context
Context is an API that allows passing of state across the app, no more need for component drilling
https://beta.reactjs.org/reference/react/useContext
https://beta.reactjs.org/learn/passing-data-deeply-with-context

It is based on a model with a context **provider** and **consumer**
- We share state from key components
- Make this state available through the context
- And the consumers can access it at will

### 3.1 Steps
- import using `import {createContext, useContext} from "react"`
- Construct  a **context** with `createContext`. This is done at the top level (not in a component)
- In our component hierarchy, we create a **provider** for that context and give it a value through its `value` property
- Component under the **Provider** can then access the value through the **useContext** hook

```JSX
// This is global, not in a component
const TempFormatContext = createContext("C");
```

THEN within the main `div` that is returned:

```JSX
// enclose entire content of div in it, if more than one, just nest further
<TempFormatContext.Provider value={tempFormat}>

</TempFormatContext.Provider>
```

THEN in the desired component:

```JSX
let tempFormat = useContext(TempFormatContext)
```

Context does not hold values, useState is still needed or toggle. It just provides different ways of accessing

