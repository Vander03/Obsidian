 
## 1 Packet Routing
Assign a range of IP addresses to each organisation while others are reserved for local networks and special purposes

### 1.1 Special Addresses: 
Network address: 131.181.0.0
Intranet Addresses:
	10.0.0.0 - 0.255.255.255
	172.16.0.0 - 172.31.255.255
	192.168.0.0 - 192.168.255.255
Local Host: 127.0.0.1

## 2 Elements of the HTTP session
An HTTP session consists of three phases:
1. Client establishes a TCP connection(or another appropriate connection if the transport layer is not TCP)
2. The client sends its request and then waits for the answer
3. The server processes the request and sends back its answer, containing a status code and the appropriate data
**Note: with HTTP/1.1 the connection is no longer closed after 3rd phase**

## 3 A basic HTTP session
- Request is initiated via TCP connection to a port on the server, default is port 80
- Server processes request and sends response
- Request must comply with these specifications:
	- https://www.w3.org/Protocols/rfc2616/rfc2616-sec5.html
- Response must comply with these specifications:
	- https://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html
	- **Note status messages in response header**

## 4 Requests
### 4.1 Request Structure
https://developer.mozilla.org/en-US/docs/Web/HTTP/Session#Sending_a_client_request
- Method and Parameters: path to resource without domain name
- The HTTP protocol used
- Subsequent headers - usually content-type
- Empty line above data block **important: must have this separator**
### 4.2 Request examples:
https://developer.mozilla.org/en-US/docs/Web/HTTP/Session#Sending_a_client_request%23Example_requests
[Note: the URLs with anchors are correct, but may not resolve properly from PPT. You can also just access them from the menus]

## 5 HTTP GET and POST Requests
- A client makes requests via HTTP to a web server
- A web server receives and responds to HTTP requests
- GET
	- Retrieving a resource, often static web page
	- most common web request
	- Idempotent - side effects do not accumulate from multiple calls
- POST
	- posting or sending some information, pushes data and triggers response from system
	- eg. HTML form
	- Not idempotent
## 6 Uniform Resource Locators (URL)
- Identify where it is located and how to access it
- General format is `<scheme>:<scheme-specific-part>`
- eg: http://www.myserver.com:80/index.html for `<scheme://<host>:<port>/<local-resource>`

### 6.1 Request Example from Mozilla Site
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


## 7 Responses
### 7.1 Response Structure
https://developer.mozilla.org/en-US/docs/Web/HTTP/Session#Structure_of_a_server_response
- Status line, HTTP version used + status code and information
- Additional HTTP headers:
	- Timestamp, type, data block size 
- Blank line above data block
- Data block
### 7.2 Response Examples
https://developer.mozilla.org/en-US/docs/Web/HTTP/Session#Examples_of_responses

### 7.3 List of useful headers
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers

### 7.4 Common Response Codes
https://developer.mozilla.org/en-US/docs/Web/HTTP/Response_codes
![](Pasted%20image%2020240313004255.png)

## 8 Dom (Document Object Model)
Web 1.0
- Platform independent model of an HTML document
- Hierarchical tree structure
- Nodes may have a parent and multiple child nodes
- Allows localised queries and updates
- No need to reload the entire document 
- Browsers provide a JavaScript binding to the DOM

