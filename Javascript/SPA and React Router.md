Not everything needs to come all the way from the server


## The Single Page App
- Browsers are essentially operating systems now
- So we load skeleton html and CSS and masses of JavaScript, then we render the page as needed
- Most of the work takes place on the client 
	- URL's intercepted and handled by the application router
	- Then render each individual component

## SPA trade-offs
- Advantages:
	- Major speed benefit, most resources re loaded initially (HTML, CSS and JS). Once loaded the application is usually very responsive to user and navigation - can support rich UI interactions and shared state between screens
	- Can be set up to work offline as the resources can be cached
	- Same backend could be used for both a web SPA and a native mobile app
- Disadvantages
	- Difficult to get search engine optimisation (SEO) right. When a web crawler visits a SPA, it usually only indexes the main page
	- Doesn't work if the user decided to disable JavaScript in their browser
	- Memory leaks can be more sever are the application can persist in the browser for a long time
	- Initial load can be slow as the browser has to fetch resources for the whole application


## Routing in React
This is **client side routing**, the REST API on the server is entirely different

Single page apps disrupt the normal conventions
- Multiple views via the one pane loaded
- We intercept and handle certain routes
- Our handlers render the page views

In general, we should have:
- Consistent URLs - the browser address window should update
- The back and forward buttons working normally
- Direct link access to a view - deep linking should work

### React Router
- Is a popular routing library that runs anywhere React runs (web, server or mobile)
- use `BrowserRouter` for the web
- Then we introduce a number of `links`
	- Links make routes available on the page
	- Organised hierarchically as with standard site designs
	- Each link should have a corresponding **route**
		- **Routes** are there to handle specific URLs or patterns
		- Routes allow us to specify element (component) responses
		- Including default error conditions


## Utility Hooks
- React Router also provides several utility hooks
	- `useParams` - access path parameters ("/country/australia")
	- `useSearchParams` - access query string parameters ("shoes?colour=black")
	- `useNavigate` - navigate to a page programatically, without including a link (e.g. a button press)
