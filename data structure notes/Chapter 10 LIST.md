## Objectives
After studying this chapter, you should be able to
- Describe the ADT list
- Use the ADT list in a Java program

#### Specification for ADT list
- you can add a new entry anywhere in the list
- you can erase an entry(remove it)
- you can remove all entries
- you can replace an entry
- look, get, an entry at a given position
- can get ALL entries
- can find if a list has a specific entry
- count # of entries in list
- see if the list is empty

### the ADT list
- a way to identify an entry in a list, is by using the entry's position within the list
	- it allows you to describe/specify the operation on a list more precise 
- an ADT list is more general and has entries that are objects of the same type

`add(newEntry): Adds a new entry to the end of the list.`
`add(newPosition, newEntry): Adds a new entry to the list at a given position.`
`remove(givenPosition): Removes the entry at a given position from the list.`
clear(): Removes all entries from the list.
`replace(givenPosition, newEntry): Replaces the entry at a given position in the list with a given position in the list with`
`getEntry(givenPosition): Retrieves the entry at a given position in the list.`
`toArray(): Retrieves all entries in the list in their current order.`
`contains(anEntry): Sees whether the list contains a given entry.`
`getLength(): Gets the number of entries in the list.`
`isEmpty(): Sees whether the list is empty.`

- to add to a list use `add()`
- to check if empty use `isEmpty()`
- ![[Pasted image 20251002222344.png]]
- you can add elements at different positions of a list with
	- `.add(2,d)` (2 is the position, d is the element)
- objects in an LIST have an order determined by client of the list
	- to add, remove, retrieve, or replace an entry specify the entry's position within the list(first entry in list is at position 1)
- to get an entry use `.getEntry()`
- to remove an element use `.remove()`
- to replace an element use `.replace(3,f)` (3 is position, f is the element)
- ADT specifications overlook/ignore situations, once you write the major portions of specifications on the ADT, you can concentrate on details that make the specifications complete
## operations
==`add(newEntry)`==:  +add(newEntry: T): void, 
- Task: adds newEntry to end of the list
- input: newEntry is an object
- Output: none
==`add(newPosition, newEntry)`==:  +add(newPosition: integer, newEntry: T ): void
- Task: adds newEntry position newPosition within the list, position 1 indicates first entry
-  input newPosition is an integer, newEntry is an object
- output: Throws exception if newPosition is invalid for this list before operation
==`remove(givenPosition)`==: +remove(givenPosition: integer): T
- task: removes and returns the entry at position `givenPosition`
- input: `givenPosition` is an integer
- output: Either retuns the removed entry or throws an exception if `givenPosition` is invalid for the list, (any value of `givenPosition` is invalid if the list is empty before operation)
==`clear()`==: +clear(): void
- task: removes all entries from the list
- input: none
- output: none
==`replace(givenPosition, newEntry)`==: +replace(givenPosition: integer, newEntry: T): T  
- **Task**: Replaces entry at position `givenPosition` with `newEntry`  
- **Input**: `givenPosition` is an integer, `newEntry` is an object  
- **Output**: Returns replaced entry, or throws exception if invalid/empty  
==`getEntry(givenPosition)`==: +getEntry(givenPosition: integer): T  
- **Task**: Retrieves the entry at position `givenPosition`  
- **Input**: `givenPosition` is an integer  
- **Output**: Returns entry, or throws exception if invalid/empty  
==`toArray()`==: +toArray(): T[]  
- **Task**: Retrieves all entries in order  
- **Input**: None  
- **Output**: Returns a new array of entries  
==`contains(anEntry)`==: +contains(anEntry: T): boolean  
- **Task**: Checks if list contains `anEntry`  
- **Input**: `anEntry` is an object  
- **Output**: Returns `true` if found, `false` otherwise  
==`getLength()`==: +getLength(): integer  
- **Task**: Gets number of entries currently in the list  
- **Input**: None  
- **Output**: Number of entries  
==`isEmpty()`==: +isEmpty(): boolean  
- **Task**: Checks if the list is empty  
- **Input**: None  
- **Output**: Returns `true` if empty, `false` otherwise  
### using list layout/program
- who should decide what `toArray` does when a collection is empty?
	- when `toArray` returns a new allocated array that contains the entries in a collection.
		- IF the collection is empty the method could
			- return an empty array
			- throw an exception
- when making a ListInterface, if toArray should return an empty array if the list is empty, making that any class that implements `ListInterface` needs to do this as well. So all clients(subclass) can expect toArray to do this
- entries in a list of `n` are numbered `1-n`. You cant add a new entry at position 0, you can add one at position n + 1

## Using the ADT List
- the technique of inserting each name into a collection of alphabetized names is called `insertion sort`
## Java class library: The Interface `List`
- the library contains an implementation of the ADT that uses a resizable array
	- the class can be called `ArrayList` and implements the interface `java.util.List`
	- can also be package `java.util.`
- you can make two constructors for `ArrayList`
	- `public ArrayList()`
		- creates an empty list with an initial capacity of 10, list increases its capacity as needed by unspecified amount
	- `public ArrayList(int initialCapacity)`
		- creates an empty list with the specified initial capacity, list increases its capacity as needed by an unspecified amount
- `java.util.vector` is similar to `ArrayList`
	- both classes implement the same interfaces(`java.util.List`)
	- vector contains a few more methods than ArrayList
- You can use either `ArrayList` or `Vector` as an implementation of the interface `List`
	- EX: you could either write the following statements to define a list of strings
		- `List<String> myList = new ArrayList<>();`
		- `List<string> myList = new Vector<>();`
			- now `myList` only has methods declared in the interface `List`
- `ListInterface` is a bit more simple than java `List` considering it has fewer methods
- you can retain simplicity of interface and make use of existing class by either using `ArrayList` or `Vector` in an implementation of `ListInterface`

## Chapter Summary

- A list is an object whose data consists of ordered entries. Each entry is identified by its position within the list.
- The ADT list specifies operations that add an entry either to the end of a list or at a given position within the list. Among its other operations are those that retrieve, remove, or replace the entry at a given position.
- A client manipulates or accesses a list’s entries by using only the operations defined for the ADT list.
- The entries in a bag are unordered, whereas the entries in a list, a stack, a queue, a deque, or a priority queue do have an order. A list, unlike these other collections, enables you to add, retrieve, remove, or replace an entry at any given position.