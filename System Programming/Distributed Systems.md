- Advantages of Distributed Systems
- Types of Network-Based Operating Systems
- Network Structure
- Communication Structure
- Design Issues

This week we will be covering Distributed Systems. A Distributed System is a collection of loosely coupled processors interconnected by a communications network. A Distributed System can also be thought of as a collection of physically separate, possibly heterogeneous, computer systems that are networked to provide users with access to the various resources that the system maintains. Access to a shared resource increases computation speed, functionality, data availability, and reliability.

Some operating systems generalise network access as a form of file access, with the details of networking contained in the network interface’s device driver. Others make users specifically invoke network functions. Generally, systems contain a mix of the two modes—for example FTP and NFS. The protocols that create a distributed system can greatly affect that system’s utility and popularity.

![500](Pasted%20image%2020230912151730.png)


## Advantages of Distributed Systems
- Resource sharing
	- Sharing and printing files at remote sites
	- Processing information in a distributed database
	- Using remote specialised hardware devices
- Computational speedup - **load sharing** or **job migration**
- Reliability
	- Detect and recover from site failure, function transfer, reintegrate failed site
- Communication
	- **Message passing** 
	- All higher level functions of a standalone system can be expanded to encompass a distributed system
Computers can be downsized, more flexibility, better user interfaces and easier maintenance by moving from large system, to multiple smaller systems performing distributed computing.


## Types of Network-Based Operating Systems
**Network-Operating System**
- Users are aware of multiple machines
- Access to resources of various machines done explicitly by:
	- Remote logging into the appropriate remote machine (telnet, ssh)
	- Remote Desktop (Microsoft Windows)
	- Transferring data from remote locations to local machines, via File Transfer Protocol (FTP)
- Users must change paradigms - establish a session, give network based commands
	- More difficult for users

**Distributed-Operating  Systems**
	- Users not aware from multiplicity of machines
		- Access to remote resources similar to access to local machines
- Data Migration - transfer data by transferring entire file, or transferring only those portions of the file necessary for the immediate task
- Computation Migration - Transfer the computation rather than the data across the system
	- via remote procedure calls (RPC's)
	- or via messaging system
- Processing Migration - execute an entire process, or parts of it, at different sites
	- **Load balancing** - Distribute processes across network to even workload
	- **Computational speedup** - subprocesses can run concurrently on different sites
	- **Hardware preference** - process execution may require specialised processor
	- **Software preference** - required software may be available at only particular site
	- **Data access** - run process remotely, rather than transfer all data locally


## Network Structure 
**Local-Area network (LAN)** - Generally considered to be at the same site, only covers small geographical area
- Multiple topologies like star or ring 
- Speeds from 1Mb per second (bluetooth, Appletalk) to 40Gbps for fastest Ethernet over twisted pair copper or optical fibre
- Consist of multiple computers (mainframes through mobile devices), peripherals (printers, storage arrays), routers (specialised network communication processors) providing access to other networks
- Ethernet most common way to construct LAN's
	- Multiaccess bus-sized
	- Defined by standard IEE 

**Wide-Area Network (WAN)** - links geographically separated sites
- Point-to-point connections over long hail lines (often leased from a phone company)
	- Implemented via routers
- Internet WAN enables hosts world side to communicate
	- Hosts differ in all dimensions but WAN allows communications 
- Speeds
	- T1 link is 1.554 Megabits per second
	- T3 is 23 x T1s = 45 Mbps
	- OC-12 is 622 Mbps
- WANs and LANs interconnect, similar to cell phone network
	- Cell phones use radio waves to cell towers
	- Towers connect to other towers and hubs

## Communications structure
The design of a communication network must address four basic issues:
- **Naming and name resolution** - How do two processes locate each other to communicate?
	- Address messages with the process-id
	- Identify processes on remote by:
		- <host-name, identifier> pair
	- **Domain name system (DNS)** - specifies the naming structure of the hosts, as well as name to address resolution (Internet)

- **Routing strategies** - How are messages sent through the network
	- **Fixed routing** - A path from A to B is specified in advance; path changes only if a hardware failure disables it
		- Since the shortest path is usually chosen, communication **costs** are minimised
		- Fixed routing cannot adapt to load changes
		- Ensures that messages will be delivered in the other in which they were sent 
	- **Virtual routing** - A path from A to B is fixed for the duration of one session. Different sessions involving message from A to B may have different paths
		- partial remedy to adapting to load changes
		- Ensures that messages will be delivered in the order in which they were sent 
	- **Dynamic routing** - The path used to send a message from site A to site B is chosen only when a message is sent
		- Usually a site sends a message to another site on the link least used at that particular time
		- Adapts to load changes by avoiding routing messages on heavily used path
		- Messages may arrive out of order
			- This problem can be remedied by appending a sequence number to each message
		- Most complex set up
		- Tradeoff means all methods are used 
			- UNIX provides ability to mix fixed and dynamic 
			- Hosts may have fixed routes and gateways connecting networks together may have dynamic routes


- **Connection strategies** - How do two processes send a sequence of messages
	- **Circuit switching** - A permanent physical link is established for the duration of the communication. ex telephone
	- **Message switching** - A temporary link is established for the duration of one message transfer. ex post-office mailing system
	- **Packet switching** - Messages of variable length are divide into fixed-length packets which are sent to destination
		- Each packet may take a different path through the network
		- The packets must be reassembled into messages as they arrive
	- Circuit switching requires setup time, but incurs less overhead for shipping each message, and may waste network bandwidth (wastes a cable if no longer used)
		- Message and packet switching require less setup time, but incur more overhead per message
	- Design issues
		- **Transparency** - the distributed system should appear as a conventional, centralised system to the user
		- **Fault tolerance** - the distributed system should continue to function in the face of failure
		- **Scalability** - as demands increase, the system should easily accept the addition of new resources to accomodate the increased demand
			- Consider Hadoop open source programming framework for processing large datasets in distributed environments (based on Google search indexing)

- **Contention** - The network is a shared resource, so how do we resolve conflicting demands for its use

# Socket Programming

A socket is an abstract representation of an "endpoint for communication"
Sockets can be either
- Connection based or connectionless
- Packed based or stream based
- Reliable or unreliable

## Sockets
Sockets are defined by their domain, type and transport protocol
**Common domains:**
- AF_UNIX: address format is UNIX pathname
- AF_INET: address format is  host and port number
**Common types:**
- virtual circuit: received in order transmitted and reliably. Virtual form of circuit based communication, always connected. , abstraction, simplifies the process "just send data across, idk how it works"
- datagram: arbitrary order, unreliable, , closer to whats actually going on
**Common transport protocol:**
- TCP/IP (virtual circuit) **connection -  based**
- UDP/IP (datagram) - **connectionless**

**Connection-based sockets** communicate client-server: the server waits for a connection from the client
**Connectionless sockets** are peer-to-peer: each process is symmetric

## BSD Socket APIs

**Connection based socket - TCP**
-  `socket`: creates a socket of a given domain, type, protocol **client/server**
-  `bind`: assigns a name to the socket **server**
-  `listen`: specifies the number of pending connections that can be queued for a server socket **server**
- `accept`: server accepts a connection request from a client **server**
- `connect`: client requests a connection to a server **client**
- `send`, `sendto`: write to connection **client/server**
-  `recv`, `recvfrom`: read from connection **client/server**
-  `shutdown`: end sending or receiving **client/server**
-  `close`: close a socket and terminate a TCP connection **client/server**
![400](Pasted%20image%2020230912184817.png)

**Connectionless Socket - UDP** - is symmetrical
- `socket` 
- `bind`
- `sendto`
- `recvfrom`
- `shutdown`
- `close`
![200](Pasted%20image%2020230912185607.png)

## Socket APIs
```c
#include <sys/types.h>
#include <sys/socket.h>
int socket(int family, int type, int protocol);
// Return: non-negative descriptor if OK, -1 on error

family:  AF_INET (IPv4 protocol) – Internet Protocol version 4
		 AF_INET6 (IPv6 protocol) - Internet Protocol version 6
		 AF_LOCAL (Unix domain protocol)
		 AF_ROUTE (Routing sockets)
		 AF_KEY (Key socket)
type:    SOCKET_STREAM (stream socket)
		 SOCKET_DGRAM (datagram socket)
		 SOCKET_SEQPACKET (sequenced packet socket)
		 SOCKET_RAW (raw socket)
protocol:IPPROTO_TCP (Transmission Control Protocol) // Protocol can be left out, can pass 0
		 IPPROTO_UDP (User Datagram Protocol)
		 IPPROTO_SCTP (Stream Control Transmission Protocol)

```

## Functions

### Bind
```c
#include <sys/types.h>
#include <sys/socket.h>

int bind(int socketfd, const struct sockaddr *myaddr, socklen_t addrlen); // Used to set options like port and method
Return: 0 if OK, -1 on error

/*struct sockaddr is a type that is compatible with the address structures of
different socket types (e.g. struct sockaddr_un for AF_UNIX, struct
sockaddr_in for AF_INET, struct sockaddr_in6 for AF_INET6). The size of
the original structure is provided via addrlen so it can be used within sockets.*/

```

## Server Code
```c
#include <stdio.h>
#include <stdlib.h>
#include <strings.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <unistd.h>
#include <netinet/in.h>
int main(int argc, char **argv)
{
	struct sockaddr_in serverAddr;

	// Steps to follow
	int listenFd = socket(AF_INET, SOCK_STREAM, 0);
	bzero(&serverAddr, sizeof(serverAddr));
	serverAddr.sin_family = AF_INET;
	serverAddr.sin_addr.s_addr = htonl(INADDR_ANY);
	serverAddr.sin_port = htons(1301);
	bind(listenFd, (struct sockaddr *)&serverAddr, sizeof(serverAddr));
	listen(listenFd, 5);
	//
	
	for (;;) {
		int connectFd = accept(listenFd, NULL, NULL);
		// ... read and write oeprations on connectFd ...
		shutdown(connectFd, 2);
		close(connectFd);
	}
	return 0;
}
```

## Client Code

```c
#include <stdio.h>
#include <stdlib.h>
#include <strings.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <unistd.h>
#include <netinet/in.h>
#include <arpa/inet.h> // important
#include <errno.h>
int main(int argc, char **argv)
{
	const char *serverName = "127.0.0.1"; // localhost
	struct sockaddr_in serverAddr;
	
	int sockFd = socket(AF_INET, SOCK_STREAM, 0);
	bzero(&serverAddr, sizeof(serverAddr));
	inet_pton(AF_INET, serverName, &serverAddr.sin_addr); // sets the address its sending to
	serverAddr.sin_family = AF_INET;
	serverAddr.sin_port = htons(1301);
	
	connect(sockFd, (struct sockaddr *)&serverAddr, sizeof(serverAddr));
	// ... read and write operations on sockFd ...
	shutdown(sockFd, 2);
	close(sockFd);
return 0;
}
```


## Endian
network numbering uses big endian (hex values up front, 39 30 00 00)
Host uses small endian (hex values at end, 00 00 30 39)
In order for us to communicate, this needs to be converted:
```c
htons(int) // Host to network, string so s for short
htonl(int) // Host to network, integer so l for long 

nthohs(int) // network to host, string so s for short - Uses less bandwidth
ntohl(int) // network to host, integer so l for long - Uses more bandwidth
```
**Note**: can send numbers as string aswel
Most of the internet is little endian

# Issues
## Sending and receiving more than one data
Because it is a stream of information, errors can be caused when the stream is closed prematurely. For eg. if a client sends data twice with a delay in between and the receiver only receives once, it will accept the initial data then close down as it is satisfied it had received that data, when the other send then sends the data an error occurs as there is no receive. Point is the receive doesn't know how much is coming.

**Fix is to abstract** - create a function, see `sendMessage` in Client Code below.
# Implementation Examples

## Server Code
```c
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <unistd.h>
#include <string.h>
#include <stdlib.h>


int main(int argc, char **argv) {
	if (argc != 2) {
		printf("\nUsage a.out <portNo>\n");
		return 1;
	}
	int bytesRcv;
	struct sockaddr clientaddr;
	socklen_t addrlen;
	char buffer[1024];
	
	struct sockaddr_in serverAddress;
	int fd = socket(AF_INET, SOCK_STREAM, 0); //0 is default for socket implementation
	if (fd==-1) {
		perror("\nsocket()\n");
		return 1;
	}
	serverAddress.sin_family = AF_INET;
	serverAddress.sin_addr.s_addr=htonl(INADDR_ANY);
	serverAddress.sin_port = htons(atoi(argv[1]));

	if (bind(fd, (struct sockaddr *)&serverAddress, sizeof(serverAddress))==-1) {
		perror("bind()");
		return 1;
	}
	int clientfd;
	
	if (listen(fd, 10)==-1) {
		perror("listen()");
		return 1;
	}
	while (1) {
		clientfd = accept(fd,&clientaddr, &addrlen );	
			
		if (clientfd==-1) {
			perror("accept()");
			return 1;
		}
				
			//1023 so can add null term if req
		bytesRcv = recv(clientfd, buffer, 1023,0);
		if (bytesRcv==-1) {
			perror("bytesrcv");
			return 1;
		}

		buffer[bytesRcv] ='\0';
		printf("\nNumber of Bytes received from client was %d.\n\nInformation sent through socket --> %s\n\n", bytesRcv, buffer);
		close(clientfd);
	}
	if (shutdown(clientfd, SHUT_RDWR) ==-1) {
		perror("shutdown()");
		return 1;
	} 
	close(fd); //sockets can remain open after program termination - when open socket should close it
}

```

## Client Code
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdint.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <unistd.h>
#include <arpa/inet.h>

void sendMessage(int fd, const char *msg)
{
    int len = strlen(msg);
    uint32_t netLen = htonl(len); // encodes length of message
    send(fd, &netLen, sizeof(netLen), 0);
    if (send(fd, msg, len, 0) != len) {
        fprintf(stderr, "send did not send all data\n");
        exit(1);
    }
}

int main()
{
    int fd = socket(AF_INET, SOCK_STREAM, 0);
    if (fd == -1) {
        perror("socket()");
        return 1;
    }

    struct sockaddr_in addr;
    memset(&addr, 0, sizeof(addr));
    if (inet_pton(AF_INET, "127.0.0.1", &addr.sin_addr) != 1) { // better way of doing this getaddrinfo()
        perror("inet_pton");
    }

    addr.sin_family = AF_INET;
    addr.sin_port = htons(12345);

    // connect
    if (connect(fd, (struct sockaddr *)&addr, sizeof(addr)) == -1) {
        perror("connect()");
        return 1;
    }

    char *dataToSend = "123456";
    sendMessage(fd, dataToSend);
    sendMessage(fd, dataToSend);

    if (shutdown(fd, SHUT_RDWR) == -1) {
        perror("shutdown()");
        return 1;
    }

    close(fd);
}

```






# Further Examples/Notes
# Server Side
Note: error checking not implemented
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h> // Not entirely necessary
#include <sys.sockets.h> 
#include <netinet/in.h>
#include <unistd.h>

int main()
{
	int fd = socket(AF_INET, SOCK_STREAM, 0); // listeing socket file descripter
	if (fd == -1){
		perror("fd()");
		exit(1);
	}
	// Setting socket options - saying its okay to reuse addr and port
	int opt_enable = 1;
	setsockopt(fd, SOL_SOCKET, SO_REUSEADDR, &opt_enable, sizeof(opt_enable));
	setsockopt(fd, SOL_SOCKET, SO_REUSEPORT, &opt_enable, sizeof(opt_enable));

	struct sockaddr_in addr;
	memset(&addr, 0, sizeof(addr)); // Wipe address to 0s
	addr.sin_addr.s_addr = htonl(INADDR_ANY); // Seting as server, others connect to us
	addr.sin_family = AF_INET; // Adress family
	addr.sin_port = htons(12345); // Set port number

	bind(fd, (struct socketaddr *)&addr, sizeof(addr));

	if (listen(fd, 10) == -1){ // Listen for input - backlog of 10
		perror("setsocket()");
		exit(1);
	}
	
	struct sockaddr_in clientaddr;
	socklen_t clientaddr_len = sizeof(clientaddr); // Size of addr

	int clientfd = accept(fd, &clientaddr, &clientaddr_len); // accept
	if (clientfd == -1){
		perror("accept()");
		exit(1);
	}
	
	// Do stuff with socket
	char buf[1024];
	int bytes_received = recv(clientfd, buf, 1023, 0); // Receive data
	if (bytes_received == -1){
		perror("receive()");
		exit(1);
	}
	
	buf[bytres_received] = '\0';
	printf("Received from client: %s", buf);

	if(shutdown(clientfd, SHUT_RDWR) == -1){ // Shut down for read/write
		perror("shutdown()");
		exit(1);
	}
	// Close descripters
	close(clientfd); 
	close(fd);
}
```
If want to continuously read data, implement an infinite loop from `int clientfd = accept(...)` to `close(clientfd);

# Client Side
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h> // Not entirely necessary
#include <sys.sockets.h> 
#include <netinet/in.h>
#include <unistd.h>
#include <arpa/inet.h>

int main()
{
	int fd = socket(AF_INET, SOCK_STREAM, 0); // file descripter
	if (fd == -1){
		perror("fd()");
		exit(1);
	}
	struct sockaddr_in addr;
	memset(&addr, 0, sizeof(addr));
	const char *ipaddress = "127.0.0.1";
	inet_pton(AF_INET, ipaddress, &addr.sin_addr) // Converts address and stores in addr.sin_addr
	addr.sin_family = AF_INET;
	addr.sin_port = htons(12345);

	if (connect(fs, (struct sockaddr *)&addr, sizeof(addr) == -1){ 
		perror("connect()");
		exit(1);
	} 

	char *dataTosend = "Hello World\n";
	if (send(fd, dataTosend, strlen(dataTosend), 0)){; // Sending data
		perror("send()");
		exit(1);
	}
	shutdown(fd, SHUT_RDWR); // Shut down
	close(fd)
}
```
## Endians Commands
```c
// Host byte order short - Host to network short
printf("htons(%d) = %d\n", <port>, htons(<port>)); 
// Host byte order long
printf("htonl(%d) = %d\n", <port>, htonl(<port>)); 
// Network byte order short 
printf("ntohs(%d) = %d\n", <port>, ntohs(<port>));
// Network byte order long
printf("ntohl(%d) = %d\n", <port>, ntohl(<port>));
```
They convert between host byte order (host machine) to the the network byte order, or vice verse Which can be either a short (`htons()`) or a long (`htonl()`).
Where byte order is how we store the data. i.e. Endianness. 
### Example
Passing a port `12345`. 
```c
htons(12345) = 14640
htonl(12345) = 959447040
htohs(12345) = 14640
ntohl(12345) = 959447040
```
In hex:  `12345 = 0x3039`. 
Little endian: `12345 = 39 30 00 00 = 14640`  
Big endian:    `12345 = 00 00 30 39 = 959447040` 

Demonstrated using unsafe casting:
```c
int val = 12345; // 4 bytes
unsigned char *cval;
cval = &val;

// Inspect values of val (bytes)
printf("%d = %x %x %x %x\n",val, cval[0], cval[1], cval[2], cval[3]);
// Prints: 12345 = 39 30 0 0
```
## Sending/Receiving Multiple Packets
Client side:
```c
// Message sending function
void sendMessage(int fd, const char *message){
	int len = strlen(msg);
	uint32_t netLen = htonl(len); // Guarentees int is always 32 bits
	send(fd, &netLen, sizeof(netLen), 0); // Send data
	if (send(fs, msg, len, 0) != len){
		fprintf(stderr, "Message was not right lenght");
		exit(1);
	}
}
char *dataToSend = "12345\n";
sendMessage(fd, dataToSend);
sleep(5); // Wait until sending next data
sendMessage(fd, dataToSend);
```
Server side:
```c
// Message receiving function
char * recvMessage(int fd){
	char *msg;
	uint32_t netLen;

	int recvLeng = recv(fd, &netLen, sizeof(netLen), 0);
	if (recv(fd, &netLen, sizeof(len), 0) != sizeof(netLen)){
		fprintf(stderr, "Recv invalid length (got %d)\n", recvLen);
		exit(1);
	}
	len = ntohl(netLen);
	msg = malloc(len + 1); // + 1 for null terminator
	if (recv(fd, msg, len, 0) != len){
		fprintf(stderr, "recv got invalid length message\n");
		exit(1);
	}
	msg[len] = '\0';

	return msg;
}
// Receiving messages
char *msg1 = recvMessage(clientfd);
printf("msg1: %s\n", msg1);
char *msg2 = recvMessage(clientfd);
printf("msg2: %s\n", msg2);

// Deallocate data
free(msg1);
free(msg2);
```
# Netcat
Used for testing network connectivity.
### Netcat client:
```c
nc localhost <port>
// Send bytes
```
Will send "Hello, World" to server
```c
echo "Hello, World" | nc localhost <port>
```
Send file data:
```c
nc localhost <port> < data.txt
```
### Netcat server:
```c
nc -l -p <port> // Bind and listen on 12345 port
```
Redirect data to file:
```c
nc -l -p <port> > out.txt
less out.txt // Read data
```