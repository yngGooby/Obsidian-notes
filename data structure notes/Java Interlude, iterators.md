iterator: enables you to step through/travel a collection of data like a list.
- you control the iteration by repeatedly asking the iterator to give you reference to the next entry in the collection
- keeps tract of where you're going in a list, lets you move through each item one by one, starting from first. you can also add, remove, or change items as you go
Using regular for loops with `getEntry()` works fine for arrays, but is slow for linked list, due to each time it has to start at the first node and walk through again.
- to fix that we make looping part of the list but only return all the items
- "you cant control what's happening while its looping" but an iterator solves that by remembering where it is in the list so you can move through, change or use the items one by one without starting over.

#### Note:
- iterator is an object that steps through or travels a collection of data. The iterator keeps track of its progress during the travel. it can tell you whether the next entry exist and if so return a reference for it. During one loop of the iteration, each data item is considered once.

# Interface `iterator`
uses generics so i can work with any data type.
- only has 3 methods: `hasNext()`, `next()`, and `remove()`
	- these let you traverse a collection from the start
	- the cursor of an iterator isnt placed directly on an entry
		- it sits before the first entry, between entries or after the last one
		- so for 'n' entries there are 'n + 1' po9ssible cursor positions
	- `hasNext()` checks if theres another entry to return
		- if true, moves the cursor to the next entry and returns it.
		- if called and there are no more entries throws a `NoSuchElementException`
	- `remove()` method deletes the entry that `next()` just returned,(optional)
		- if not supported must throw `UnsupportedOperationException`
		- can also throw `illegalStatementException` if used incorrectly(like before calling next twice in a row)
- all the exceptions are runtime exceptions, so no need to throws or try/catch. But import `NoSuchElementException` from java.uti
- the Iterable interface lets a collection create and return its own iterator using the `iterator()` method.
	- any class that implements Iterable can use an enhanced for loop
		- i.e `for(String name : nameList)`
		- since the loop automatically calls the `iterator()` method to step through the collection.
## using the interface iterator
- you get an iterator from a list using
	- `Iterator<String> nameOfIter = nameList.iterator();`
		- when created, the iterator starts JUST BEFORE THE FIRST ENTRY in the list. The methods `hasNext()` and `next()` work together to move through the entries. `hasNext()` checks if there's another element to visit, and `next()` moves the iterator forward and returns that element. Like a loop
 `while(nameOfIter.hasNext())` 
 - will display every entry in order, one by one until the iterator reaches the end of the list
 The method `remove()` lets the iterator DELETE THE LAST ENTRY RETURNED by `next()` must follow a rule set...
 - Must call `next()` before using remove(),
 - cant call `remove()` twice after the same next()
	 - will cause `IllegalStateException`
- calling `next()` when no entries remain 
	- cause a `NoSuchElementException`
you can have MULTIPLE ITERATORS working on the same list at once. Each iterator moves by itself
- one iterator could point to a name while another goes through the list counting how many times the name appears.
- can lead to repeated counting if the same name occurs more than once
- if `remove()` is supported, duplicates can be removed as they're found to avoid extra work

## Using the interface ListIterator
you can create a list iterator using
	`ListIterator<String> traverse = nameList.listIterator()`
- when first created, the iterator starts AT THE BEGINNING of the list, before the first entry
if the list contains: 
	-Jess
	- Jim
	- josh
checking the iterator's status gives:
- nextIndex: 0
- hasNext: true;
- previousIndex: -1;
- hasPrevious: false;
calling `next()` moves the iterator forward and returns the next entry while `previous()` moves it back and returns the one before
- example
	- after calling `next()` once the iterator moves past "Jess", `nextIndex` becomes 1, calling `previous()` then moves it back and returns "Jess" again
- these methods let you move `foward and backward` through a list, one entry at a time
to display a list in `reverse order` you could first move the iterator to the end of the list and keep calling `previous()` while `hasPrevious()` is true

## the `set` Method
the `set()` method replaces the LAST ENTRY RETURNED by `next()` or `previous()`
- example
	- `traverse.set("Jen")`
- replaces "Jess" with "Jen" in the list, resulting in
	- Jen
	- Jim
	- Josh
the iterator's position doesnt change after the replacement, `nextIndex` and `previousIndex` stay the same.
You can call `set()` again to replace another value but it must always follow a call to `next()` or `previous()` and not come right after `add()` or `remove()`

## the `add` Method
`add()` method inserts a NEW ENTRY RIGHT BEFORE  the iterator's current position.
if the iterator is between "Jen" and "Jim" and you call
- `traverse.add("Ashley)`
	- the list becomes
		- Jen
		- Ashley
		- Jim
		- Josh
after adding `next()` still returns "Jim"(sane entry it would have before) but `previous()` now returns "Ashley" the insertion also **shifts the indices forward by one**, so after the addition, `nextIndex` becomes 2 and `previousIndex` becomes 1

## The `remove` Method
`remove()` in a `listIterator` works like the one in Iterator but responds to both `next()` and `previous()`. It removes whichever entry was returned by the most recent call to either of those methods.
- example if the list is 
	- Jen
	- Ashley
	- Jim
	- Josh
- and the iterator between "Ashley" and "jim" calling
	- `traverse.previous()`
	- `traverse.remove()`
- removes "Ashley" from the list, leaving
	- Jen
	- Jim
	- Josh
- the iterator's position remains just before "Jim"
both `set()` and `remove()` throw `IllegalStateException` if you try to call them before `next()` or `previous()`, or if `remove()` or `add()` was already called after the last movement
- in short
	- `next()` and `previous()` move forward and backward.
	- `set()` changes the last entry you accessed.
	- `add()` inserts a new entry before the current spot.    
	- `remove()` deletes the last entry returned by `next()` or `previous()`.  
    All these methods make `ListIterator` flexible for **navigating and editing lists** in both directions.

### **The Interface List Revisited (J4.18)**

The `java.util.List` interface (which you first saw in Chapter 10) **extends Iterable**, meaning it already includes the **`iterator()`** method. In addition, it provides two versions of **`listIterator()`**, shown below:
```
public ListIterator<T> listIterator(int index);
public ListIterator<T> listIterator();
```
Both methods return a **ListIterator**, which can move **forward and backward** through the list and modify it during traversal.
- The version with an **index parameter** starts the iterator at the **given position**, where index `0` refers to the **first entry**.
- The version without parameters is the same as calling `listIterator(0)`, which starts **at the beginning** of the list.
Since the standard collection classes — **ArrayList**, **LinkedList**, and **Vector** — all implement the **List** interface, they include both **`listIterator()`** methods, along with the regular **`iterator()`** method inherited from Iterable.

**In short:** `List` adds support for **ListIterators**, which allow more flexible and directional traversal than a regular iterator, and all major list classes in `java.util` implement these methods.