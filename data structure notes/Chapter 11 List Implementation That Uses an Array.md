
## Objectives
After studying this chapter, you should be able to
- Implement the ADT list by using an array that you can resize
- Discuss the advantages and disadvantages of the implementation presented

#### using array to implement the ADT List
- ### java implementation
	- with the implementation, since java already has an `ArrayList` with that name you chose different names to avoid confusion
	- heres a list of things you need for the ADT list class
		- array of objects
		- integer that counts the number of entries in the list
		- integer constant that defines default capacity of list
		- integer constant that defines max capacity of list
		- boolean flag that indicates if list is properly initialized
		- ![[Pasted image 20251006001756.png]]
	- Which array elements should contain the list?
		- we place a list first entry in `List[1]` and kth entry in `List[K]` making it not not use and ignore the array element `List[0]`. Doing so will result in a minor waste of space but lead to intuitive implementation.
	- note
		- due to `AList` constructors, create a list whose capacity is at least `DEFAULT_CAPACITY,` the method `add` can assume that the array has sufficient space for the first addition to the list

## Layout of the class `AList`
```java
import java.util.Arrays;

/**
 * A class that implements a list of objects by using an array.
 * Entries in a list have positions that begin with 1.
 * Duplicate entries are allowed.
 */
public class AList<T> implements ListInterface<T> {

    private T[] list;                     // Array of list entries; ignore list[0]
    private int numberOfEntries;
    private boolean integrityOK;
    private static final int DEFAULT_CAPACITY = 25;
    private static final int MAX_CAPACITY = 10000;

    /** Default constructor */
    public AList() {
        this(DEFAULT_CAPACITY);           // Call next constructor
    }

    /** Constructor with capacity parameter */
    public AList(int initialCapacity) {
        integrityOK = false;

        // Ensure capacity is within bounds
        if (initialCapacity < DEFAULT_CAPACITY)
            initialCapacity = DEFAULT_CAPACITY;
        else
            checkCapacity(initialCapacity);

        // Safe cast: new array contains null entries
        @SuppressWarnings("unchecked")
        T[] tempList = (T[]) new Object[initialCapacity + 1];
        list = tempList;
        numberOfEntries = 0;
        integrityOK = true;
    }

    /** Adds an entry to the end of the list */
    public void add(T newEntry) {
        checkIntegrity();
        list[numberOfEntries + 1] = newEntry;
        numberOfEntries++;
        ensureCapacity();
    }

    /** Adds an entry at a specific position */
    public void add(int givenPosition, T newEntry) {
        // < Implementation deferred >
    }

    /** Removes the entry at a given position */
    public T remove(int givenPosition) {
        // < Implementation deferred >
        return null;
    }

    /** Clears all entries from the list */
    public void clear() {
        // < Implementation deferred >
    }

    /** Replaces an entry at a given position */
    public T replace(int givenPosition, T newEntry) {
        // < Implementation deferred >
        return null;
    }

    /** Retrieves the entry at a given position */
    public T getEntry(int givenPosition) {
        // < Implementation deferred >
        return null;
    }

    /** Converts the list to a new array */
    public T[] toArray() {
        checkIntegrity();

        @SuppressWarnings("unchecked")
        T[] result = (T[]) new Object[numberOfEntries];
        for (int index = 0; index < numberOfEntries; index++)
            result[index] = list[index + 1];

        return result;
    }

    /** Checks if the list contains a specific entry */
    public boolean contains(T anEntry) {
        // < Implementation deferred >
        return false;
    }

    /** Gets the current length of the list */
    public int getLength() {
        return numberOfEntries;
    }

    /** Checks if the list is empty */
    public boolean isEmpty() {
        return numberOfEntries == 0; // Or getLength() == 0
    }

    /** Doubles the capacity of the array list if it is full */
    // Precondition: checkIntegrity has been called.
    private void ensureCapacity() {
        int capacity = list.length - 1;
        if (numberOfEntries >= capacity) {
            int newCapacity = 2 * capacity;
            checkCapacity(newCapacity);
            list = Arrays.copyOf(list, newCapacity + 1);
        }
    }

    // < This class will define checkCapacity, checkIntegrity,
    //   and two more private methods that will be discussed later. >
}
yes```
- the `add` method and the `toArray` were added before other due to them being central /core to the class. 
	- adding a new entry to the end of a list involves
		- add the entry to the array immediately after its las occupied location
- adding new entry is possible only if the array has available space.
- adding to the beginning of an array-based list is O(n) adding to the end is O(1)
	- if the array isnt resized, its O(n)
	- time required to add at other positions depends on the position
	- as position # increases, time needed for addition decreases
- you can use a vector to contain entries in a list, java class vector uses an array in its implementation, vector based implementation of list will be array based, uses a resizable array to contain the list entries
	- can resized and grow as needed
- in an ADT list, using an array or vector 
	- retrieving an entry at a given position is O(1)
	- adding an entry at the end is o(1)
	- add or remove an entry between other entries shifts them within the array
	- increasing size of array or vector, you need to copy entries 
**when to Call `ensureCapacity()`:**
- Run it **after adding** an entry instead of before, so the array is always ready for the _next_ addition.
- This allows expansion to happen in the background (possible multithreading later).
- Constructors already guarantee enough space for the first addition.