## Objectives
After studying this chapter, you should be able to
- Describe a linked organization of data
- Implement the ADT list by using a linked chain of nodes
- Discuss the advantages and disadvantages of the implementation presented
- Compare and contrast the array-based and link-based implementations of the ADT list

## adding a node at various positions
- to add a node at a specific place, consider...
	- case 1: chain is empty
	- case 2: adding a node at the chains beginning
	- case 3: adding a node between adjacent nodes
	- case 4: adding a node to the chain's end
- ### note: 
	- adding a node between adjacent nodes of a chain
		- you must be able to add a node to a chain between two existing, consecutive nodes
	-         `newNode references the new node`
`			Place newEntry in newNode`
`			Let nodeBefore reference the node that will be before the new node`
`			Set nodeAfter to nodeBefore’s link`
`			Set newNode’s link to nodeAfter`
`			Set nodeBefore’s link to newNode``

case 1: adding a node to an empty chain
		newNode references a new instance of Node
		Place newEntry in newNode
		firstNode = address of newNode
			- first node is blank and new node has data
				- firstNode is now assigned to newNode
case 2: adding a node to the beginning of a chain
		newNode references a new instance of Node
		Place newEntry in newNode
		Set newNode’s link to firstNode
		Set firstNode to newNode
			- new node is now the first node
				- while the new node is created and first node is pointed to the original value, after adding the new node to the start of the chain new node becomes first and first node points to new node, the old value is now pushed forward
				- Node newNode = new Node(newEntry);
				  newNode.setNextNode(firstNode);
				  firstNode = newNode;
					- the actual entries are removed from the list, the entries are objects that the nodes reference
case 3: adding a node between adjacent nodes of a chain
- since ADT list doesn't allow additions between two existing entries, must be able to add a node to a chain between two existing consecutive nodes
			newNode references the new node
			Place newEntry in newNode
			Let nodeBefore reference the node that will be before the new node
			Set nodeAfter to nodeBefore’s link
			Set newNode’s link to nodeAfter
			Set nodeBefore’s link to newNode
	- to insert a new node somewhere in a linked list, you need to find the spot where it should go, number each node starting from 1(the positions)
	- method getNodeAt(int givenPos) helps with returning a node at a specific position in the list. Since its only used inside the list class and restricted for outside access should be made private
case 4: adding a node to the end of a chain, to add a node to the end of an existing chain
		newNode references a new instance of Node
		Place newEntry in newNode
		Locate the last node in the chain
		Place the address of newNode in this last node
			-make the last node in the chain ref the new node.
#### Note:
	adding a new node to the end of a chain of "n" nodes can be like adding the node at position 'n + 1'

#### note: 
- adding a node to an empty chain is the same as adding a node to the beginning of the chain

## removing a node from various positions

- to remove a node at a specified position, consider the two cases
	- case 1: removing the first node
	- case 2: removing a node other than the first one
case 1: the steps you take are
	Set firstNode to the link in the first node; firstNode now either references the second node o
	Since all references to the first node no longer exist, the system automatically recycles
	the first node’s memory.
		- the first node is now the next node in the list
		- first --> [A] --> [B] -->
		- first (skips A) --> [B]
		- `firstNode = firstNode.getNextNode();`
case 2: removing a node other than the first one. remove a node at a position other than the start of the chain. The steps are
	Let nodeBefore reference the node before the one to be removed.
	Set nodeToRemove to nodeBefore’s link; nodeToRemove now references the node to be removed.
	Set nodeAfter to nodeToRemove’s link; nodeAfter now either references the node after the one to be removed or is null.
	Set nodeBefore’s link to nodeAfter. (nodeToRemove is now disconnected from the chain.)
	Set nodeToRemove to null.
	Since all references to the disconnected node no longer exist, the system automatically recycles the node’s memory
			- with the node before and the node after it, once the node that you want to remove is removed, the node before now points to the node after.
### private method `getNodeAt`
returns a reference to the node at a given position in the chain.
	// Returns a reference to the node at a given position.
	// Precondition: The chain is not empty;
	// 1 <= givenPosition <= numberOfNodes.
	`private Node getNodeAt(int givenPosition)`
to locate a specific node start at the first node and go one by one.
use temp variables (`currentNode`) to ref nodes one at a time when going down the chain.
setting current node to firstNode so it references the first node in the chain.
	- if seeking first node code is executed otherwise keep going down the chain
		- `currentNode = currentNode.getNextNode();`
	- if you need the 2nd node its done, else keep going by using
		- `currentNode = currentNode.getNextNode();`
	- keep going until you reach the position needed within the list
```
private Node getNodeAt(int givenPosition){
Assertion: (firstNode != null) && (1 <= givenPosition) && (givenPosition <= numberOfNodes)

Node currentNode = firstNode;
// Traverse the chain to locate the desired node
// (skipped if givenPosition is 1)

for (int counter = 1; counter < givenPosition; counter++)
currentNode = currentNode.getNextNode();

// Assertion: currentNode != null
return currentNode;
} // end getNodeAt
``` 
in the for loop the currentNode is never null if the preconditions are met.
	- which makes `currentNode.getNextNode` never execute if currentNode is null
	- assert statement during the testing of getNodeAt verity's the claims
## Starting the implementation
- Design Decision: How should we efficiently construct the chain of linked nodes?
- if you keep adding items to the end of a linked list one by one the program has to start at the first node and go through the entire list every time.
	- to fix that issues you keep a tail reference(a pointer to the last node) so when adding a new item you instantly connect it to the end without traversing the chain
- list are a bit more difficult to maintain with both head and tail pointers compared to queues.
	- recommended to use the head ref first, once that works fine add the tail reference later to make adding items faster.
## Data fields and constructor 
The constructor and `Clear()` both reset the list
its best to keep them separated so future changes to `Clear()`don't affect object creation
also with the constructor something like 
```
public LList(){
	first = null;
	numOfEntries = 0;
}
```

## Adding to the end of the list
- when using the add method to insert an item at the end of a linked list the code:
	- -**Makes a new node** with your data.
	- **Checks if the list is empty** — if it is, that node becomes the first one.
	- If it’s **not empty**, it uses `getNodeAt(numberOfEntries)` to **find the last node** and link the new one after it.
	- Finally, it **increases the count** of items in the list.
- adding at the end of a singly linked list means traveling from the head to the last node before adding the new one