# The Stacks Data Structure

## Definition:

A collection of entities maintained in a sequence that can be modified by the addition `push` of entities at one end and removal `pop` of entities at the same end.

- Think of a deck of cards or a stack of plates:
- You have to remove a plate from the very top of the stack to get to a plate down below
- You can only add plates to the top of the stack

![Image of a Basic Stack](https://i.imgur.com/YWJiSxP.jpg)

## Key Nuggets:

- Last In, First Out (LIFO): Last element to be added is the first element to be removed
- What this means: The “top” of the stack is the “back”, the “bottom” of the stack is the “front”. In the image above, C must be removed before B can be removed. Because C was the Last In, it is also the First Out.

## Methods:

- `push()` - push an element into the back of the stack (i.e. Last In)
- `pop()` - pop an element out from the back of the stack

## Implementation: Washing Dishes

If you’re washing dishes and have a stack of dirty plates, then you have to wash each plate, one at a time, from the top of the stack first, before reaching the bottom most plate.

```js
class Stack {
  constructor() {
    this.data = [];
  }
  push(record) {
    this.data.push(record);
  }
  pop() {
    return this.data.pop();
  }
  peek() {
    return this.data[this.data.length - 1];
  }
}
```

## Under the Hood

Here, we’ve instantiated a Stack class object. In the constructor, we’ve included a data property set to an empty array. This means that every instance of a Stack will start out with an empty array at the `data` property. The array will store some data.

The `push()` method adds a record, or data, to the top of the stack.
The `pop()` method removes the last record from the stack.

Remember: The last data pushed into the stack is the first to be removed.

The `peek` method “peeks” into the stack and returns the last element of the stack _without_ removing it. This method comes in handy when traversing or manipulating a stack and you have to check the last value in the collection without removing or manipulating it. Remember, you start at the top of the stack (i.e. the last element) and traverse down.
