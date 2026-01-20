### linked implementation
- if we use a chain of linked nodes to implement a stack, where in the chain should we place the stack's top entry
	- if we only have the chains head reference we can remove or access its first node faster than any other node, thus the stack operation will execute fastest if the first node in the chain references the top entry in the stack![[Pasted image 20250915152251.png]]
	-`user input/understanding of statement`
		from what i can read its saying if we have a chain stack we can use the head reference which i assume is the first item in the stack, we can remove other links with access to the first node which makes execution faster
- in a linked implementation operators work differently
- ==`pop`==: just moves to the next node but saves the previous nodes data. OR updates the head reference of the next node of the chain and returns saved data(it still removes the headnode from the chain)
- ==`push`==: creates new node also stores an entry in it, links its `next` to the current head finally moves the head reference to the new one
- ==`peek`==: looks at data stored in the head node then returns that value(does not change the head)
- ==Nodes== are allocated when created only when needed for a new entry.
- ==Nodes== are deallocated when an entry is removed
		- java runtime environment automatically reclaims, deallocates memory that a program no longer references, without instruction from the programmer
- if using chain of linked nodes to implement a stack, first node should reference stacks top entry

## security note: implementation guidelines
- use assertions to verify assumptions
- when verifying data, check that it is valid instead of invalid
- verify return values given to you, especially those provided by code you didn't write

## Array based implementation
issues with implementing an array with stack is 
- *if you make the first array slot hold the top of the stack, then every time you push or pop you have to shift all the other items forward or backwards in the array which is inefficient.* 
	- A better way to approach this 
		- make the first array slot hold the bottom of the stack (first entry)
		- top of the stack is just the last filled slot in the array
		- when pushed you drop a new value into the next empty slot
		- when pop you removed from the last slot used
		- everything stays in place no shifting needed
	- if using array to implement stack, array's first element references the bottom of the stack. The last occupied element in the array then references the stacks top entry
### Vector based implementation
- ==Vector==: object that behaves like a high level array.
	- vectors entries are indexed beginning with 0, like an array but difference is vector has no methods to set/access its entries. you can create a vector of a given size and itll grow in size as needed