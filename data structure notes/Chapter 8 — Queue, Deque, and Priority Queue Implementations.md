
Objectives
After studying this chapter, you should be able to
- Implement the ADT queue by using either a chain of linked nodes or an array
- Add or remove nodes at either end of a chain of doubly linked nodes
- Implement the ADT deque by using a chain of doubly linked nodes
- Implement the ADT priority queue by using either an array or a chain of linked nodes
### linked implementation of a queue
- adding a tail reference(external reference) to the last node in the chain is one way to solve inefficient traversing of a linked queue
- to not traverse the entire chain, we make the chains first node contain the queues front entry
	- placing the front of the queue at the start of the chain forces the back of the queue to the chains end.
		- since adding entries only to the back of the queue due to adding a tail reference for the chain. the arrangement works
```
/**
 * 🧩 A class that implements a **queue of objects** using
 * a **chain of linked nodes**.
 */
public final class LinkedQueue<T> implements QueueInterface<T> {

    // 🔗 References node at front of queue
    private Node firstNode; 
    
    // 🔚 References node at back of queue
    private Node lastNode;  

    // 🏗️ Default constructor
    public LinkedQueue() {
        firstNode = null;
        lastNode = null;
    } // end default constructor

    // ⚙️ Implementations of the queue operations go here
    // enqueue, dequeue, getFront, isEmpty, clear, etc.
    // ...

    // 🧱 Inner Node class
    private class Node {
        private T data;      // 💾 Entry in queue
        private Node next;   // 🔗 Link to next node

        // 🧰 Constructors and methods:
        // getData, setData, getNextNode, setNextNode
        // ...
    } // end Node
} // end LinkedQueue
```
- before adding a new node to an empty chain the firstNode and lastNode have nowhere to reference
- when creating a new node before addition
	- the last node is still the tail reference 
- during the addition 
	- the new node is added in and the previous node now references back to it
- after addition
	- the new node is now the tail reference
- a queue is empty if the `firstNode && lastNode == null` or if a firstNode == newNode(if the head and tail refer to the same node)
	- the operation is O(1)
- Why is a tail reference desirable when you use a chain of linked nodes to implement a queue?
	- being able to add new entries to the back of the queue in O(1) time without having to traverse the chain
## A Circular Array
- The behavior of the array acts like a circle
	- the first element follows its last one
- once the queue reaches the end of the array, you can remove entries to the queue at the start of the array
- to use a circular array use the modulo arithmetic.
	- when adding entry to the queue increment `backIndex` modulo the size of the array
- `backIndex = (backIndex + 1) % queue.length` (to add to the back)
- to remove an entry, add `frontIndex` modulo the size of the array
	- `frontIndex = (frontIndex + 1) % queue.length`
- "When we removed an entry from an array-based bag in Chapter 2 , we replaced the removed entry with the last one in the array. Yet the implementation of the queue just described does not do so. Explain this difference in implementations"
	- with bag all that was needed is to add a new element to fill in said gap, but with queue you must follow the FIFO rule
- to detect if the circular array is full, it happens when `frontIndex == backIndex + 1`
- 