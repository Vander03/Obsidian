- A linear data structure has elements arranged in a linear manner
- Each element except for the first and last element in the data structure has a previous element and a next element
- Examples:
	- Array
	- Linked List
	- Stack
	- Queue

## Array
- Elementary linear data structure
- A (one-dimensional) array is a sequence of *n* items of the same data type, that are stored contiguously in computer memory
- An item in an array is accessible by index
- In most cases the index is an integer between 0 and *n* -1 
- Every element of an array can be accessed in the same constant amount of time in a computer regardless of where in the array the element in question is located
- Arrays can be used for implementing a variety of other data structures

## Linked List
- A linked list is a sequence of zero or more elements called **nodes**, each containing an item and one or two links called **pointers** to other nodes of the linked list.
- A special pointer called *null* is to indicate no link
- In a **single** linked list, each node except for the last one contains a single pointer to the next node
	- ![500](Pasted%20image%2020240316162737.png)
- In a **double** linked list, each node except for the first and last contains a pointer to its successor and a pointer to its predecessor 
	- ![500](Pasted%20image%2020240316162747.png)
- The pointer to a linked list (that is, the pointer to the first node in the linked list) is stored in a seperate location
- A linked list is a **dynamic data structure**
	- A **dynamic data** structure refers to a type of data structure that can change in size during the execution of a program. Unlike static data structures (which have their size determined at compile time)
	- This includes the allocation and deallocation of memory as objects are added or removed
- The length is determined by the number of nodes in the list

## Array vs Linked List
- Both array and linked list can be used to implement a more abstract data structure **list**, which is a sequence of items
- The basic operations performed on lists are accessing, searching for, inserting and deleting an item
	- To access the $K^{th}$ entry in an array or a linked list
		- In an array, accessed using an index `item[k]`
		- In a linked list, we must step through the first `k-1` nodes
- To insert an item into the beginning of an array or linked list
	- In an array, we must move all the elements in the array before we can insert the item, which is not efficient enough for large arrays
	- ![500](Pasted%20image%2020240316184507.png)
	- In a linked list, we can directly insert the item into the beginning of the linked list, which is efficient
	- ![500](Pasted%20image%2020240316184546.png)
- To delete an item from an array or linked list
	- In an array, we must move all the items after the deleted item in an array
	- In a linked list, we do not need to move any item, but we need to traverse the pointer chain to find the pointer to the predecessor, and the pointer to the successor, of the node containing the item to be deleted
- To search an item in an array or linked list
	- In an array we can search the array sequentially or use binary search if the elements in the array are sorted
	- In a linked list we need to traverse the pointe chain to find the node where the item is sorted

## Stack
- A **stack** is a linear data structure that stores items sequentially and allows access to the top only
- Adding an item
	- Referred to as **pushing** it onto the stack
- Removing an item
	- Referred to as **popping** it from the stack
- Items stored in a stack are kept in a pile
	- When an item is pushed to the stack it is placed on top of the pile
	- When an item is taken from the stack, it is always the top item
- A stack is a LIFO (Last In First Out) data structure

![500](Pasted%20image%2020240316203659.png)

### Applications of Stack
- Stacks can be used to check **parenthesis matching** in an expression
- Stacks can be used for **expression evaluation**
- Stacks van be used for **conversion** from one expression to another
- Stacks can be used for **memory management**
- Stacks can be used in **backtracking algorithms**


## Queue
- A queue is a linear data structure that allows certain operations on both ends
- Can be implemented as an array or linked list
- Middle items cannot be accessed directly
- Queues are restricted versions of arrays and linked lists
- It provides one operation, **Enqueue**, to add an item to the data structure, and an operation **Dequeue** to remove an item from the data structure
- Items are added into a queue at one end of the queue (tail) and items are removed out of a queue at the other end of the queue (head)
- A queue is FIFO (first in first out)

![500](Pasted%20image%2020240316211847.png)

### Applications of queue
- **Algorithm design**
- **CPU scheduling**
- **Disk scheduling**
- **managing shared resources between various processors**
- **data transferring between IO buffers (input and output buffers)**
