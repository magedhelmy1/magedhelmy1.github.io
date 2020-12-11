---
title: Stack and Queue
date: 2019-08-01 14:00:00 +0100
categories: [Blogging, Computer Science]
tags: [data_structures]
---

## Stacks

An abstract data structure is defined by a set of values and set of operations. The abstract is used to perform different operations that are abstracted from the user. In other words, an abstract data type is an abstraction of a data structure which provides only the interface to which a data structure must adhere to.

A stack is an abstract data type which allows operations at one end only. We can place or remove a card or plate from the top of the stack only. Also, all data operations occur at one end only, we can only access the top element of a stack.  This feature makes it a LIFO data structure, where LIFO stands for Last-in-first-out.  The element is inserted as a push operation and removed using a pop operation.

When pushing data, we can use peek() to get the top data element of the stack, isFull() to check if stack is fully, isEmpty() to check if stack is empty.

At all points, we maintain an index to the last pushed data on the stack. The top value is thus the last object.

The push operation is the process of adding a data element on the stack.

1)	Checks if the stack is full
2)	If stack is full, produces an error and exit
3)	If the stack is not full, increments top to the point next empty space
4)	Adds data element to the stack location where top is pointing
5)	Returns success

The pop operation, the data element is not actually move, instead top is decremented to a lower position in the stack. In a linked list, pop removes data element and deallocates memory space.

1)	Check if the stack is empty
2)	If empty, produce an error and exit
3)	If the stack is not empty, access the data element at the top
4)	Decrease the value of top by 1
5)	Return success

pop: O(1)
push: O(1)
peek: O(1)
lookup: O(1)

Do we build Stacks with Arrays or Linked Lists ?
- Both will work fairly well. With some advantage and disadvantage.
- With arrays it is faster since items are next to each other, linked list are scattered all over the memory. Also they need extra spaced since they store the reference.
- With linkedlist though, you can dynamically increase the data without having to worry bout the cost while with an array you have to double the space, and re-index when increasing your list.

## Queue

Similar to stacks, Queue is an abstract data structure, unlike stacks, a queue is open at both ends. One end is always used to inset data and the is used to remove data. This is First-in-first out methodology.

Queue representation: -> Data in-> Queue -> Data out. As in stacks, a queue can be also implemented using arrays, linked-lists, pointers and structures.

The basic operations of a queue are:
-	Enqueue()- add an item to the queue O(1)
-	Dequeue()- remove an item from the queue O(1)
-	Peek()- get the element at the front of the queue without removing it O(1)
-	Isfull()- check if the queue is full
-	Isempty()- check if the queue is empty

In queue, we always dequeue (or access) data, pointed by front pointer and while enqueing (or storing) data in the queue we take help of rear pointer.

Creating a Queue from arrays is inefficient since you have to shift everything in the list. With Queue it is an O(1) operation while in arrays it is an O(n) operations.

Do we build Quees with Arrays or Linked Lists ?
- Always build with linked list. Since arrays have indexes associated with them. Since index shifting has to occur when adding data.
