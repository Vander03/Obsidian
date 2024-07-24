## 1 Callbacks and promises
### 1.1 Asynchronous calls
- Something else is running so we arrange to call a function when it is finished
- JS environments are single threaded

### 1.2 Three main approaches
- Callback functions in the parameter list **old style**
	- `oldButton.addEventListener("click", () => [callback function here])`
	- Callbacks are functions that are called back once something has happened  
- Promises that chain responses together **new style**
- Async and wait (equivalent to promises)
 
## 2 Node Callback
- Callbacks allow a function to respond when its complete. You pass it whatever you need run in the future.
- The function is invoked with the error object, if present, and the result
- All based on convention, it is expected to be called in a certain way but theres no guarantees as the order, or arguments to the function rely on the API. 

Function that runs only when a request is received, common in node servers
`server.on('request', function (request, response) ) (function here)`

**Example implementation:**
```JavaScript
// old style
doRequest('https://google.com', (error, result) => {
	if (error != null) {
		// by convention error will be null if theres no error
		handleError()
		return
	}

	handleResult(result)

})
```

## 3 Fetch()
- JS function that is supported in the browser and node. 
- **GET** request by nature
- Returns a **promise**
	- We don't know **when**, or **if**, the server is going to respond and we deal with this uncertainty by issuing a **promise**.
	
## 4 Promises
Promises are a way to manage uncertainty
- Promises can succeed or fail but:
	- They can only do one or the other, and they can only do it **once**
	- Once a promise succeeds **it stays successful**
	- Once a promise fails, **it remains a failure**
- The more formal terminology:
	- **fulfilled** - the action relating to the promise succeeded
	- **rejected** - the action relating to the promise failed
	- **pending** - hasn't fulfilled or rejected yet
	- **settled** - has fulfilled or rejected
Fetch data from JSON or elsewhere, then do these functions. If the call fails, catch the error and print function

#### 4.1.1 Misusing a promise
1. Placing a catch before continue could result in undefined behaviour as the then has no idea if an error has occurred or not.
2. Due to the code being asynchronous, avoid assigning any external variables inside of the scope of the promise, as the behaviour may be undefined because the code isn't guaranteed to have been executed.
3. If a fetch is returned, the next .then will wait on that fetch to complete and the original promise will be lost. This can be used to chain one promise off another. In general there should try not to nest within promises
	1. ![500](Pasted%20image%2020240410232227.png)

#### 4.1.2 Advanced Uses
![800](Pasted%20image%2020240410233830.png)
A promise is static once its created and its value cannot be changed, however we can make our promises more useful. If we wrap them in a function that does extra work, if the promise is returned from our function then other functions can chain onto it and execute more code.

Here, we wrap the `doRequest` function we’ve been using previously
Now we can attach some more useful information to it.
Our users don’t even need to know about the `doRequest` function
They can just use `makeRequest` and continue as before, now with a handy error code.

**NOTE:** this is a good situation to catch before the final usage, if we know what the errors will be we can provide the user more useful information instead of them catching it themselves. If we DONT know what the error will be we can throw the same error again (causing the promise to reject again). DO NOT HIDE ERRORS


```js
// GET example
fetch("https://jsonplaceholder.typicode.com/posts")
	.then(function(response) {
		if (response.ok) {
			return response.json();
		}
		throw new Error('Network response was not ok.');
	})
	.then(function(result) {
		let newDiv = document.getElementById("new");
		newDiv.innerHTML = JSON.stringify(result);
	})
	.catch(function(error) {
		console.log('Problem with your fetch operation: ', error.message);
	});
```

```js
// POST example
const postButton = document.getElementById("postBtn");
postButton.addEventListener("click", () => {
	fetch("https://jsonplaceholder.typicode.com/posts", {
		method: 'POST',
		body: JSON.stringify({
			title: 'Lucy the Golden',
			body: 'Lucy Dog',
			userId: 1
		}),
		headers: {
			"Content-type": "application/json; charset=UTF-8"
		}
	});
	.then(function(response) {
		if (response.ok) {
			return response.json();
		}
		throw new Error('Network response was not ok.');
	});
	.then(function(result) {
		let postDiv = document.getElementById("post");
		postDiv.innerHTML = JSON.stringify(result);
	});
	.catch(function(error) {
		console.log('Problem with fetch: ', error.message);
	});
});
```

### 4.2 Making a Promise
This is the simplest way of making a promise, although it will only happen once. **Note** that a promise **doesn't have to contain asynchronous code**, but it only makes sense in an asynchronous context.

**NOTE: DO NOT CALL BOTH, only the first will count**. 
- A syntax error in the promise will cause a promise to reject. 
- Nothing we return from inside the promise constructor is used, we NEED to call resolve and call things back that way
```Javascript
/*
Call the promise constructor, pass function which creates the promise, of which there are 2 arguments, a "resolve" function and a "reject" function. Do all the work you need then call resolve, or if theres an error and we have control over it, call "reject"

*/
new Promise((resolve, reject) => {
	// do something here that is asynchronous
	if (error) {
		// if something went wrong with async part
		reject(error);
	} else {
		// assuming 'result' has the data we want
		resolve(result);
	}
});
```
##### 4.2.1.1 This is a more useful implementation
![700](Pasted%20image%2020240411131136.png)
## 5 Curl
Way to retrieve data from websites, included in unix
`$ curl https://google.com/`

## 6 Async/Await
- Alternative to promises
- They do the exact same thing just different syntaxes

### 6.1 Async Def
```Javascript
// async marks the function as asynchronous, this function will return a promise every time
async function makeRequest(url) {
	try {
	// when interpreter reaches await, it suspends execution until promise is resolved
		cont result = await doRequest(url); // await can only be used inside async functions, put it in front of promise values
		return { statusCode: 200, body: result };	
	} catch (e) {
		if (e.fromServer) {
			return { statusCode: 500, error: e };
		}
		throw e;
	}
}
```
#### 6.1.1 Async Method
```JSX
<html>
	<script>
		let a = async () => {
			let response = await fetch("api link here"); // call api data
			let json = await response.json(); // waits for response and converts to json when received
			let text = json.data[0].email; // field found by visually inspecting API format or datasheet
			document,getElementsByTagName("body")[0].appendChild(document.createTextNode(text)); // creates html child and mounts it to body
		};
		a().then(() => {}); // call function to exeute 
	</script>
</html>
```

## 7 Performance
If there are no dependencies, aim to have all the promises happen at the same time, we should wait for them all to work simultaneously and only pause when waiting for them all to be done

For this purpose there is a utility called `Promise.all` that takes an array of promises and returns a new promise that only revolves when all of the promises have completed. If any of the promises fail there is a short circuit and you drop straight to the catch block and don't wait for all the promises to finish. **If we have multiple promises that don't depend on each other for data, use this it will speed up execution a lot**

![700](Pasted%20image%2020240411140807.png)
## 8 AJAX
- Redefines browser/server relationship
- Uses `XMLHttpRequest()`
	- note that `fetch()` is better, since it returns a promise
- Often used to send and receive JSON data