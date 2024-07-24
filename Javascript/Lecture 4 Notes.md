Receiving input:
```JSX
return (
	<div className="App">
		<form method="POST" onSubmit={
			e => {
				e.preventDefault(); // prevents default use
				window.alert("Hello there" + name); // shows alert
			}
			<input type="text" name="name" value={name} onChange={
				e => {
					setName(e.target.value); // calls state to the new value entered  
				}
			}>
		}> // could also be method GET
	</div>
)
```

## 1 Naming conventions
- It is common to put all contexts in the same folder, so they can be imported at any time
- It is common to name the file the same thing as the component in it
- 