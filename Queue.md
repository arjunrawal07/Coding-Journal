# The Queue Data Structure
#Queue

* Definition: A collection of entities maintained in a sequence that can be modified by the addition (/enqueue/) of entities at one end and removal (/dequeue/) of entities at the other end. 
	* Think of a ticketing counter: 
		* You can’t cut the line (well, you aren’t supposed to)
		* The order of the line dictates who gets out first

[image:FA850CD3-1C78-48D1-8EB2-8377620ABF5A-6734-0000240220FA9276/Untitled presentation.png]

* *_Key Nuggets_ *:
	* *First In First Out (FIFO):* First element added to the queue is the first element to be removed
		* /What this means:/ All elements that come /before/ the element to be removed must be removed first.
			* *In the image below, A must be removed before B can be removed*
			
[image:24EB244C-9FB0-4FEF-96CE-5D53C8988A48-6734-000024726344592F/Untitled presentation-2.png]

* *_Methods_ *: 
	* add() - equivalent to .unshift()
	* remove() - equivalent  to .pop()

** _Implementation: Chipotle, Cava, Subway _*
	Say you’re at a Chipotle or Cava, where the staff assemble orders in the sequence of customers who arrive. You are waiting for your turn to let the first employee know what kind of grains you want in your meal before moving on to meats, veggies, and toppings.  You have entered the queue.

```js
class Queue {
constructor() {
	this.data = [];
}
add(order){
	this.data.unshift(order);
}
remove() {
	return this.data.pop()
}
}
```

* *Under the Hood:*
Here, we’ve instantiated a class Queue. In the constructor, we’ve included a data property set to an empty array. This means that every instance of a Queue will start out with an empty array at the `data` property. We’ve set the property to an empty array to store the orders, or data, that are submitted.

The `add()` method adds an order to the beginning of the queue.
The `remove()` method removes the last order in the queue. 

The wording here is a bit tricky, but in the context of our example, when an order is first submitted, it’s placed at the beginning of the queue (i.e. the end of the line). 

The remove method removes the order at the end of the queue (i.e. the front of the line). To get to a data point later in the queue, you have to remove all the pieces of data that come before it first (i.e. the data ahead of it in the line).