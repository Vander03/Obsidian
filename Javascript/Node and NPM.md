## 1 Node.JS
- Node is fundamentally a JS compiler and run-time
- We grab modules we need using `require`, which is different from `import` 
- Node.js is a server side JavaScript introduced to support rapid server side connections and processing

### 1.1 Key advantages of Node
- Fast - compiled and optimised
- Asynchronous JavaScript connection processing
- We don't allocate a new thread for each new connection
- It is open source with a very active developer community

#### 1.1.1 Node Example
![](Pasted%20image%2020240417115326.png)

### 1.2 Node Ecosystem and Packages
### 1.3 package.json
- Usually create a new package file at the start of development. 
- Use `npm init` and accept defaults 
- `npm install` will automatically save dependencies as we install (used to need --save)
- This records the precise version of the packages used
- We can avoid this with `--no-save` (but better to keep it)
	- `npm install mysql2 ––no-save `
- Need to consider the three tiered versioning system


### 1.4 Semantic Versioning Rules
- Node conforms o semantic versioning (semver) rules:
- Versions: `{Major}.{Minor}.{Patch}`
- Accept is what we should allow and how strict the version required is
- Patch release, increment last number
	- Includes bug fixes and other minor changes
	- Accept patch level updates: 1.0 or 1.0.x or ~1.0.4
- Minor release, increment the middle number
	- New features which don't break any existing features
	- Accept minor release level updates 1 or 1.x or ^1.0.4
- Major release, increment the first number
	- Changes which breaks backwards compatibility
	- Accept major release level updates: * or x

#### 1.4.1 Nighttime Possum Meandering (npm)
- Install globally (`-g` installation)
- Simplest use is to make other packages available
	- Installed using `npm install <package-name>`, globally is `npm install <package-name> -g`
	- Packages stored in `node_modules` directory
	- Dependencies shown in `package.json`

#### 1.4.2 MySQL
- Use `npm install mysql2`
- `package.json`
	- As of npm 5, `nom install mysql2 --save` is the default and rather `--no-save` was adde din the case that you want to install a package without adding it as a dependency

##### 1.4.2.1 MySQL example code
![](Pasted%20image%2020240417120514.png)


## 2 REST and Connecting Services
- REST is a set of principles that define how web standards, such as HTTP and URIs are supposed to be used.
- Alignment of application and web architectures

### 2.1 Key Principles of REST
- Give everything an ID
- Link things together
	- "Hypermedia as the engine of application state"
	- Global URIs allow almost unbounded linkage of resources and attributes
	- URLs can also capture **state**, allowing state transitions to be mapped to *link* transitions (changes reflect in the links)
	- This is to allow statelessness and stateless applications
- Use standard methods
	- Use Standard Methods:
		- Mainly means HTTP
		- GET, PUT, POST, DELETE (usually GET and PUT)
- Resources with multiple representations
	- Allow resources to be received and transported in formats that suits the applications
	- JSON vs XML being the standard example
- Communicate statelessly
	- Keep the state in the URI or in the client. Dont store the state in such a way that would make it problematic if connection was lost

## 3 Express
### 3.1 Express Hello World
```Javascript
var express = require('express');
var app = express();

const hostname = '127.0.0.1';
const port = 3000;

// this means that any get request, from the root of the site downwards, is handled by this function
app.get('/', function (req, res) {
	res.send('Hello World!');
});

app.listen(port, function() {
	console.log('Express app listenting on htpp://$(hostname):$(port)/');
})
```

### 3.2 Routes and Methods
https://expressjs.com/en/guide/routing.html

#### 3.2.1 Examples:
**Simple matches:**
```Javascript
// This route path will match requests to /about
app.get('./about', function (req, res) {
	res.send('about');
});
```

**Regex:**
```Javascript
// This route path will match `butterfly` and `dragonfly`, but not `butterflyman` or `dragonfly man`
app.get(/.*fly&/, function(req, res) {
	res.send('./fly$/');
});
```

### 3.3 Route Handling


### 3.4 Express Generator
To install globally, not recommended:
```console
npm install express -g
npm install express-generator -g
```

## 4 JWT
### 4.1 Authentication
Authentication is the process of establishing identity, which includes users, hosts and services (were mainly concerned with users)
- Most commonly, we authenticate a user through a password or two factor process (password+sms code)
- Login needs to be persistent, don't want users logging in for each new request

### 4.2 JSON web tokens
#### 4.2.1 Header
A JSON object containing:
- The type of the token
- The algorithm used for the signature
#### 4.2.2 Signature
Used to verify that access was given by US
- Apply a hashing algorithm to the encoded header and payload, using a secret key unknown to the users
- Signature is sent with encoded header and payload
- Allows us to identify the token as secure
- Never decoded
![500](Pasted%20image%2020240421172055.png)

#### 4.2.3 Using the token
Whenever the user wants to access a protected route or resource, the user agent should sent the JWT using the **Authorisation** header using the **Bearer** schema:
`Authorisation: Bearer <token>`

#### 4.2.4 Obtaining the token on the client
```Javascript
fetch(${SERVER_URL}/users/login, {
	method: "POST",
	headers: {
		"Content-Type": "application/json", 
	},
	body: JSON.stringify({
		email,
		password,
	}),
})
	.then((res) => res.json())
	.then((data) => {
		//parse data response and grab the token
	})
```

#### 4.2.5 Using the token in client requests
IF the route requires authentication, you need a header.
The server will parse the `Authorisation` header and verify that the token is valid and within date.
```Javascript
fetch(`${SERVER_URL}/api/people${role}`, {
	headers: {
		Authorisation: "Bearer" + token,
	},
})
	.then((res) => res.json())
	.then((data) => {
		//do stuff
	})
```

## 5 Refreshing tokens
NOT NEEDED AND NOT APPLIED IN ASSIGNMENT:
While this is not covered in the above video and not used in the assignment, refresh tokens are an important topic when it comes to maintaining the security of authorisation tokens.

One thing that is a significant problem in web security is the need to keep authorisation tokens secure. To an attacker, authorisation tokens are nearly as good as a username and password, as they provide access to the resources the attacker wants to access, and due to their nature (being stored in browser storage, being passed to every service on the site that requires authorisation) they are usually much easier to obtain. This means that authorisation tokens present a security hole that attackers can potentially exploit - by themselves, they are not necessarily a problem, but combined with some other security flaw, they become an easy way for an attacker to gain access.

There are some things we can already do to make refresh tokens a little more secure - they are often combined with some other information, like a cookie with HttpOnly set, such that if the token is stolen in a cross-site scripting (XSS) attack, it is useless to the attacker. However, ultimately, just having the token exist for a long period of time without expiring is a fundamental weakness.

We could just reduce the lifetime of the token to a very short period - seconds, minutes - but this would then require the user to log in again repeatedly, which is likely to put users off and cause them to stop visiting your site. Another alternative is refresh tokens. Conceptually, these are fairly simple - when you log in, you are given an authorisation token and a refresh token. The authorisation token is given a very short expiration period, while the refresh token is given a much longer one. Then, when you attempt to make use of a resource, if the authorisation token has expired, the browser will instead connect to the authentication provider and send the refresh token. In response, the authentication provider will send back an authorisation token and a refresh token, as though the user had logged in with username and password again.

Refresh tokens have the following advantages over long-expiring authorisation tokens:

- Refresh tokens are only sent to the authentication provider. This means that, if our site is divided up across multiple servers, we can have one of them handling authentication and we can focus our efforts on securing that particular provider. In addition, it also means that there is only one endpoint that could be attached to steal refresh tokens, as opposed to having many possible endpoints that require authorisation tokens to be sent. Preventing XSS attacks on one endpoint is far less work than preventing it on all of them. We can also provide additional security by having our cookie with additional required information marked Secure so it will only be sent to the authentication provider, reducing the potential vectors for cross-site request forgery (CSRF) attacks.
- Refresh tokens can only be used once - when a refresh token is issued, the server keeps track of it (e.g. in a database) and when it is used, the refresh token is replaced with another. This means that refresh tokens change just as frequently as our authorisation tokens do now, reducing the potential window to steal one and use it maliciously. This means refresh tokens cannot be stateless, but we still gain some of the benefits from having the authorisation tokens be stateless and the refresh tokens not be; we only have to hit the database when reauthorising, not with every transaction. This also has security benefits, as the number of machines that need to connect to the database where all this stuff is stored is reduced.
