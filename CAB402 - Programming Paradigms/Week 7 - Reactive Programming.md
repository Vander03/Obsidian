## 1 Theory
Declarative programming paradigm where when something happens, something else gets automatically updated. A graph of dependencies where change events are propagated along edges of the graph. This allows programming with asynchronous data streams.

![[Pasted image 20250419002849.png|500]]
“Functional reactive programming (FRP) is a programming paradigm for reactive programming (asynchronous dataflow programming) using the building blocks of functional programming (e.g. map, reduce and filter)”.

## 2 Reactive Manifesto
![[Pasted image 20250501222631.png|600]]
https://www.reactivemanifesto.org/
- Responsive – system responds in a timely manner
- Resilient – stay responsive in the face of failure
- Elastic – continues to work reliably even as the workload increases.
- Message Driven – asynchronous message passing to ensure loose coupling
## 3 Functional Reactive Programming

## 4 Reactive Extensions
- (IEnumerable, IEnumerator) = “pull based” Collections
	- Consumer pulls values from the collection as they are needed.
- Rx (IObservable, IObserver) = “push based” Collections
	- Producer pushes values at the consumer as they become available
	- E.g. event streams, asynchronous computations (or even normal IEnumerable collections)
### 4.1 Rx.NET

![[Pasted image 20250419003716.png|500]]

Rx (The Reactive Extension) is a library for composing asynchronous and event-based programs using observable sequences and LINQ-style query operators.
Because observable sequences are data streams, you can query them using standard LINQ query operators implemented by the Observable extension methods.
- Thus you can filter, project, aggregate, compose and perform time-based operations on multiple events easily by using these standard LINQ operators.

#### 4.1.1 Push Collections (IObservable and IObserver)
```F#
interface IObservable<out T>
{
	public IDisposable Subscribe (IObserver<out T> observer);
}

interface IObserver<in T>
{
	public void OnCompleted ();
	public void OnError (Exception error);
	public void OnNext (T value);
}
```

#### 4.1.2 System.Reactive.LINQ
![[Pasted image 20250419003849.png]]

#### 4.1.3 Observable Operator Examples
![[Pasted image 20250419003942.png]]

## 5 UI Frameworks

---
### 5.1 ReactiveUI
A functional reactive Model-View-ViewModel (MVVM) framework for .NET

### 5.2 MVVM (Model-View-ViewModel)
![[Pasted image 20250501223404.png|500]]
- ViewModel is an abstracted version of the View
	- Observable properties expose the data that should be presented (somehow)
	- Reactive commands expose actions that the user might perform (somehow)
	- Can be tested in isolation (via scripts) as no actual GUI interaction is required.

![[Pasted image 20250501223502.png]]


---
### 5.3 React.JS
#### 5.3.1 React Components
-  Model-View-Controller (MVC) and Model-View-ViewModel (MVVM) separate concerns by separating Presentation and Logic
- React separates concerns by creating separate components (widgets) that each combine presentation and logic.
	- Rendering logic (how the data is displayed)
	- How events are handled
	- How the state changes over time
This allows the UI to be split into independent, reusable pieces
Properties are provided once a react component is created it **cannot be changed, and is therefore immutable**
All react functions act like pure functions with respect to their props.
However, component state is **mutable**, and can thus be re-rendered or have its state changed in the existing instance.

#### 5.3.2 React State
DO NOT modify state directly. There are functions provided by react to modify the state. This allows react to batch multiple `setState()` calls into a single update. State updates don't have to update the entire state, only the affected parts.

#### 5.3.3 Virtual DOM and Re-rendering
![[Pasted image 20250501223917.png|500]]

#### 5.3.4 Sharing Data between React Components
Each React component encapsulates its own state. A parent component should not know whether its child components are stateful or stateless.

Date flows down from parent components to the child components via properties.
Child components then use these props to initialise their own internal state.

If two siblings both need to update the same state, the state needs to be lifted and stored in the parent, which then provides a callback function for updating the state 

---
### 5.4 Redux
Instead of each component having its own state, state is stored in a state container. Makes it easy to share state since theyre all stored in the same location independent of a parent. 

When multiple components are asynchronously updating the same state, the centralised view makes it easier to reason and ensure consistency. 
This is easier to test and debug since we can trace the updates that occurred and the order in which they were applied 

#### 5.4.1 Redux Store
![[Pasted image 20250508171044.png]]

#### 5.4.2 Redux Actions
Redux actions have a type property and a optional payload describing the details of the state change to be performed. Actions are passed to the store by calling `store.dispatch(action)`
![[Pasted image 20250508174048.png|300]]

#### 5.4.3 Reducer Function
Reducer functions are the only way to update the state of the store.
It is a pure function that takes the current state and an action to be performed and returns what will become the new updated state of the store.
![[Pasted image 20250508174105.png|300]]
In general, state stored in the store will be a single value that contains different properties that can be independently updated:
![[Pasted image 20250508174159.png|300]]

#### 5.4.4 Splitting Reducer Logic
To prevent one reducer containing all logic, we use a **root reducer** that delegates to a collection of sub reducers:

![[Pasted image 20250508174407.png|300]]

Another common approach of decomposing a reducer is by dividing state into slices and having a seperate reducer for each slice. A given action can therefore involve several slice reducers which each update different parts of the state.

![[Pasted image 20250508174653.png|300]]
^ is a example of an higher-order reducer that combines a list of slice reducers and returns a new reducer function.

#### 5.4.5 Creating and Accessing the Store
Store is typically created in the root component. The `createStore` function takes as an argument the root reducer function:
![[Pasted image 20250508175010.png|300]]

The provider component allows all nested components access to the store (without having to pass it down via properties).

![[Pasted image 20250508175122.png]]

## 6 React Native
Can write most of the application in pure javascript. 
The javascript runs inside an application native to that framework (IOS or Android)

kotlin is replacing Java on android
 


