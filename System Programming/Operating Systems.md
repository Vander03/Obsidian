## Services
- User Interface
- Program Execution
- I/O Operations
- File-System Manipulation
- Communications 
	- Processes share information either locally or over a network
	- May be via shared memory or  through message passing (packets moved by OS)
- Error Detection
	- Can occur in CPU, memory hardware, I/O devices, user program
	- OS needs to take appropriate action based on the error and provide the user with effective debugging facilities
- Resource Allocation
- Accounting 
	- Keep track of which users use how much and what kind of resources
- Protection and Security
	- Protection - Ensure that all access to system resources are controlled
	- Security - using user authentication, defending I/O from invalid access attempts
## Interface
<<<<<<< HEAD
![600](Pasted%20image%2020230801120525.png)
=======
![](Pasted%20image%2020230801120525.png)
>>>>>>> origin/main
- Command Line (CLI)
	- Sometimes implemented via kernel or system program
	- Can have multiple "flavours" named shells
	- Implements user written programs or build in commands 
- Graphics User Interface (GUI)
	- User friendly, windows etc
	- Invented at XEROX
	- Many systems have both CLI and GUI (command shell is CLI for example)
	- Mac OS X is Aqua GUI and UNIX kernel
	- UNIX and LINUX both are CLI with optional GUI
- Batch
## System Calls
- Programming interface to the services provided by the OS
- Written in high level language
- Accessed by programs using a high level API (Application Programming Interface)
	- Most common API's include:
	- Win32 API for Windows
	- POSIX API for POSIX based systems (aka all versions of UNIX, LINUX and MAC OSX) and Java in JVM
- C commands can invoke a system call (open and fopen, arent system calls themselves, rather they invoke them)
- ## System call implementation
	- ![](Pasted%20image%2020230801120600.png)
	- A number is associated with different systems calls (System-Call Interface maintains a table with all the system calls)
	- System call Interface invokes a system call in the kernel and returns status of system call and any return values
	- Caller doesnt need to know how the API was implemented, just follow instructions (API managed by runtime support library)
	- Sometimes parameters of system calls are too big, and thus needs to be written to a place in memory and pass the address. Could also push parameters onto stack
	- ![](Pasted%20image%2020230801121029.png)
## Programs
- Provides a convenient environment for program development and execution, Divided into:
	- File Manipulation 
		- create, delete, copy, rename, print, dump, list, manipulate files and directories
	- Status information stored in File modification
		- Some ask system for info: date, time, disk space, users, available memory
		- Other provide logging, debugging and performance information
		- these programs format and print to the terminal or other output devices
		- some implement and use a registry to store and retrieve configuration information
		- Text editors create and modify files
		- special commands to search or perform modifications to text
	- Programming language support
		- compilers, assemblers, debuggers, and interpreters sometimes provided
	- Program loading and execution
		- absolute loaders, relocatable loaders, linkage editors, and overlay-loaders, debugging systems for higher-level and machine language
	- Communications
		- create virtual connections between users, processes, computer systems
		- allow users to send messages, use web services, log in remotely, transfer files from one machine to another
	- Background services
		- Launch at boot time
			- Some only for startup, then terminate
			- Others from startup to shutdown
		- Services like disk checking, process scheduling, error logging, printing 
		- Run in user context not kernel context
		- Known as services, subsystems, daemons
	- Application Programs
		- Not system
		- run by users
		- not part of OS
		- launched by command line, mouse, click, finger poke
## Structure
- MS-DOS
	- ![](Pasted%20image%2020230801130658.png)
- UNIX
	- ![](Pasted%20image%2020230801131227.png)
	- Created because other operating systems were too feature rich for hardware
	- Consists of 2 parts:
		- Systems Programs 
		- The kernel
			- Consists of everything below system call interface and above physical hardware
			- Provides the file system, CPU scheduling, memory management, and other operating-system functions; a large number of functions for one level		
- Layered Approach
	- ![300](Pasted%20image%2020230801131834.png)
	- Each is built on top of lower layers
	- With modularity the system is build so that each layer only uses functions from the previous layer
	- As you write code lower and lower to the hardware the consequences of a mistake magnifies
- Microkernel
	- ![](Pasted%20image%2020230801132957.png)
	- Moves as much from the kernel to user space 
	- Mach (Mac OS X is based on this) uses microkernel
	- communication between user modules using message passing

	- Benefits
		- Easy to extend
		- more secure
		- easier to port OS to new architecture 
		- more reliable (less code running in kernel)
	- Drawbacks
		- Performance overhead due to the need for message communication
- Modules
	- Solaris Modular Approach ![](Pasted%20image%2020230801133512.png)
	- Most operating systems use loadable kernel modules
		- uses object-orientated approach
		- each core component is seperate
		- each talks to others over know interfaces 
		- each is loadable as needed within the kernel
		- Similar to layers but more flexible 
			- used by Linux, Solaris, etc
- Hybrid Systems
	- Most systems use hybrid systems to address security, performance and usability needs
	- Linux and Solaris kernels in kernel address space, so monolithic, plus modular for dynamic loading functionality
	- Windows mostly monolithic, plus microkernel for different subsystems
	- Apple Mac OS X hybrid, layered, Aqua UI plus Cocoa programming environment
		- Below is kernel consisting of Mach microkernel and BSD Unix parts, plus I/O kit and dynamically loadable modules
	- Apple Mobile OS
		- Cocoa touch objective-c API for developing apps
		- Media services layer for graphics audio etc
		- Core services for cloud computing, databases
	- Android 
		- Open source
		- based on linux kernel but modified 
			- Provides processes, memory, device driver management
			- adds power management
		- similar stack to IOS





