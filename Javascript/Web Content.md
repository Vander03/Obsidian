 
## Packet Routing
Assign a range of IP addresses to each organisation while others are reserved for local networks and special purposes

### Special Addresses: 
Network address: 131.181.0.0
Intranet Addresses:
	10.0.0.0 - 0.255.255.255
	172.16.0.0 - 172.31.255.255
	192.168.0.0 - 192.168.255.255
Local Host: 127.0.0.1

## HTTP GET and POST Requests
- A client makes requests via HTTP to a web server
- A web server receives and responds to HTTP requests
- GET
	- Retrieving a resource, often static web page
	- most common web request
- POST
	- posting or sending some information
	- eg. HTML form
## Uniform Resource Locators (URL)
- Identify where it is located and how to access it
- General format is `<scheme>:<scheme-specific-part>`
- eg: http://www.myserver.com:80/index.html for `<scheme://<host>:<port>/<local-resource>`

### Request Example from Mozilla Site
```
// simple web page grab but french preferred
GET / HTTP/1.1 // ask for HTTP version 1.1
Host: developer.mozilla.org
Accept-Lanuage: fr
```

```
// posting data from a form
POST /contact_form.php HTTP/1.1
Host: developer.mozilla.org
Content-Length: 64
Content-Type: application/x-www-form-urlencoded

name=<name of user here>
```

## Dom (Document Object Model)
Web 1.0
- Platform independent model of an HTML document
- Hierarchical tree structure
- Nodes may have a parent and multiple child nodes
- Allows localised queries and updates
- No need to reload the entire document 
- Browsers provide a JavaScript binding to the DOM

