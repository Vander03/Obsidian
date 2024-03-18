## Callbacks and promises
### Asynchronous calls
- Something else is running so we arrange to call a function when it is finished
- JS environments are single threaded

### Three main approaches
- Callback functions in the parameter list **old style**
	- `oldButton.addEventListener("click", () => [callback function here])`
	- Callbacks are functions that are called back once something has happened  
- Promises that chain responses together **new style**
- Async and wait (equivalent to promises)
 
## Node Callback

Function that runs only when a request is received, common in node servers
`server.on('request', function (request, response) ) (function here)`

## Fetch()
- JS function that is supported in the browser and node. 
- **GET** request by nature
- Returns a **promise**
	- We don't know **when**, or **if**, the server is going to respond and we deal with this uncertainty by issuing a **promise**.
	
## Promises
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
## Curl
Way to retrieve data from websites, included in unix
`$ curl https://google.com/`

## Async Method
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

## AJAX
- Redefines browser/server relationship
- Uses `XMLHttpRequest()`
	- note that `fetch()` is better, since it returns a promise
- Often used to send and receive JSON data