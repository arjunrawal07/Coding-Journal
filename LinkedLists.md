# Linked Lists

## Definition: 
An ordered collection of data with nodes. In a singly linked list, each node contain data and information about the next node.  In a doubly linked list, each node points to the next and previous node.

## Key Nuggets:
* *Head* - the first node of a linked list
* *Tail* - the last node of a linked list. No reference to any other node
* Each node is like a bucket of data with a reference to the node after it
	


![Basic Diagram of a Singly Linked List](https://i.imgur.com/3dlptq5.jpg)

## Implementation: Node + LinkedList w/Methods
Linked Lists can be used in many cases. For example, web-browsers utilize linked lists to store the data of webpages you have visited. This makes it easy to access your browsing history as the browser simply fetches the previous node’s data that is stored in the list.

## Under The Hood: Creating a LinkedList
1. We’ll begin by implementing a Node class first.
```js
class Node {
    //Set 'next' to a default of null in case no 'next' node is passed into a new instance
	constructor(data, next = null) {
		this.data = data
		this.next = null
	}
}
```

2. Next, implement a LinkedList class.
```js
class LinkedList {
	constructor() {
		this.head = null
	}
}
```

3. In the LinkedList class, write an `insertFirst()` method that assigns the head node. Then, write a `size()` method that returns the number of nodes in the list.
```js
class LinkedList {
	constructor() {
		this.head = null
	}
insertFirst (data) {
    //Method takes in some data and we pass in the only existing node of the LinkedList as the 'next' node (defined in the Node Class constructor above)
		this.head = new Node (data, this.head)
	}
size() {
	//Initialize a counter to keep track of number of nodes
		let counter = 0
	//Define a reference to the head node
		let node  = this.head
	//While ‘node’ is truthy, count
		while(node) {
		//increment the counter by one
			counter++
		//assign the next node in the list as the value of ‘node’
			node = node.next
		}
	//Once the while loop condition is no longer truthy (i.e. when node.next = null), return the number of nodes
		return counter
	}
}
```