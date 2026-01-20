
### organizing java methods that sort arrays
- sorting methods are best grouped into ***single utility class***(like `sortArray`) using ***static methods*** for reusability
- **`Generics`**(`<T>`) allows sorting methods to handle arrays of ***any object type***
- to be sortable, elements must **implement the `Comparable` interface***, which defines how objects are compared through `compareTo()`
- The generic bound `<T extends Comparable<T>>` ensures that the array's element can be compared with another
- A more flexible version `<T extends comparable<? super T>>` allows comparison involving *`superclass`* of `T`, improving type compatibility
- Typical method structure for a sorting class
- `public static <T extends Comparable <? super T>> void sort(T[] a, int n) `
		this foundations allows different `sorting algorithms` (like selection, insertion, or shell sort) to be added as separate static methods within the same class

## Selection sort
- `Selection sort` repeatedly finds the `smallest element` in the unsorted portion of an array and `swaps` it into correct positions at the front
- the process divides the array into two parts
	- a `sorted section` (on the left)
	- an `unsorted section` (on the right)
- On each pass, the algorithm selects the **`minimum value`** from the unsorted part and exchanges it with the first unsorted position
- This method uses ***uses only one array***, no extra storage by swapping values ***in place***
- in java terms, if `a` is the array:
	- Find the smallest element and swap it with `a[0]`
	- Then, find the next smallest and swap it with `a[1]`, and continue until the array is sorted
- called ***selection sort*** due to the algorithm ***selecting*** the smallest remaining element in each pass
- Sorting process performs ***n - 1 passes***, since the last element naturally ends up in place
- ***Space efficiency*** uses o(1) additional memory (in-place)
- ***Main limitation*** though simple, its **slow for large datasets** because it still requires many comparison and swaps (is O(n^2) time complex)

## Iterative selection sort
- ***Iterative selection sort algorithm*** repeatedly selects the smallest element from the unsorted portion of the array and swaps it into place using a ***for loop*** that runs ***n - 1*** times
- during each iteration, the ***index of the smallest value*** (from `a[index]` through `a[n - 1]` is found and swapped with the current `a[index]`
- after each pass, the sorted portion of the array grows from left to right: 
	- `a[0] <= a[1] <= a[index]`
- the ***last element*** `a[n - 1]` doesn't need to be checked explicitly, because it will automatically end up in the correct position once all earlier elements are sorted
- the algorithm **works in place** it only rearranges elements inside the same array without creating another one
- Supporting methods in java
	- `getIndexOfSmallest(a, first, last)` scans a range of the array to find and return the ***index*** of the smallest value
	- `swap(a, i , j)` exchanges two entries in the array; doesn't require `compareTo()` since its a direct value swap
- use generics types with ***comparable*** ensures that the sorting logic can be applied to **any comparable object**, not just primitive types
## Recursive selection sort
- ***recursive selection sort*** works the same as a iterative version but uses ***recursion*** to handle progressively smaller portions of the array
- it uses ***two parameters***, `first` and `last` to define the portion of the array being sorted `a[first]` through `a[last]`
- ***Base case*** when `first == last` the array has one element so no sorting is needed
- ***Recursive case***
	- find the index of the **smallest value** in the current range `a[first]` to `a[last]`
	- ***Swap*** it with `a[first]` to place it in its correct position
	- ***Recursively call*** the method to sort the remaining part of the array `a[first + 1] ` through `a[last]`
- Example structure
		`if (first < last){ 
			`int indexOfNextSmallest = getIndexOfSmallest(a, first, last)`;
			`swap(a, first, indexOfNextSmallest);`
			`selectionSort(a, first + 1, last);`
		}

- a **wrapper method+** can call the recursive method like this:
		`selectionSort(a, 0, n - 1);`
- The recursive design offers **clarity** and **cleaner logic flow** through it performs the same number of comparisons and swaps as the iterative version (has a On^2 run time)
- future sorting algorithms will adopt the **three parameter structure** `(a, first, last)` to generalize operations over portions of an array
## The efficiency of selection sort
- selection sort runs with O(n^2) time because it repeatedly scans through the array to find the smallest element for each position
- the ***outer loop*** executes `n-1 times` each time calling `getIndexOfSmallest()` and `swap()`
- in each call to `getIndexOfSmallest()` the ***inner loop*** runs `(last - first)` times, which decreases from `n - 1` to **1** as sorting progresses
- the total number of comparisons add up to
	- `(n-1)+(n-2)+...+1 = n(n-1) / 2`
		- means the number of operations grows proportionally to the ***square of n***
- because each comparison and swap is O(1)  the entire algorithm remains O(n^2) regardless of whether the array is **sorted, reversed, or random**
- the recursive version performs the same steps and has the ***same efficiency***
- both versions are ***in place algorithms*** using ***O(1) extra space***, meaning no additional arrays are needed
#### note: 
- selection sort s ***O(n2)*** regardless of the initial order of the entries in an array, though sort requires ***O(n2)*** comparisons, it preforms only ***O(n)*** swaps, thus the selection sort requires little data movement

## insertion sort
- insertion sort ***builds a sorted section*** of the array one element at a time
- each new value from the unsorted part is ***inserted into its correct position*** in the sorted part by shifting larger elements to the right
- the array effectively splits into two parts
	- ***sorted region***: starts with the first element
	- ***unsorted region***: the remaining elements
- after every pass, one more element joins the sorted region, so the sorted side grows while the unsorted side shrinks
- the process continues until the entire array is sorted
	- EX pattern
		- Start: `[9 | 6 2 4 8]`
		- insert `6` -> `[6 9 | 2 4 8]`
		- insert `2` -> `[2 6 9 | 4 8]`
		- insert `4` -> `[2 4 6 9 | 8]`
		- insert `8` -> `[2 4 6 8 9]`
	- **Efficiency:**
		- time complexity: ***O(n^2)*** worse case, ***O(n)*** if nearly sorted
		- space: ***O(1)*** `in place sorting`
- performs fewer movements than selection sort when the list is almost in order, making it better for ***small or mostly sorted datasets***

### iterative insertion sort
- ***insertion sort*** divides an array into two parts
	- ***sorted region***: starting with the first element 
	- ***unsorted region*** the rest of the array
-  on each pass, then algorithm removes the ***first element of the unsorted region*** called `nextToInsert` and places it into the correct position within the sorted region
- the ***`insertInOrder()`*** helper method compares `nextToInsert` with elements in the sorted region from **right to left, shifting** larger elements one position to the right until the correct position is found
- each iteration expands the sorted region by one element and reduces the unsorted region by one, continuing until all elements are sorted
- in pseudocode
	- ```
	  for(unsorted = first + 1; unsorted <= last; unsorted++){
		  nextToInsert = a[unsorted];
		  insertInOrder(nextToInsert, a, first, unsorted - 1);
	  }
	  ```
- The `insertInOrder()` process:
	- starts at the end of the sorted portion `index = end`
	- while `anEntry < a[index]` a shift the larger value to the right (`a[index + 1] = a[index]`)
	- insert the value once the correct position is found (`a[index + 1] = anEntry`)
### The Efficiency of Insertion Sort
- ***insertion sort runs in O(n^2)*** time in the **worst case**, due to each new element needing to be compared and shifted against all previous elements
- The ***outer loop*** executes ***`n-1`*** times and the ***inner shifting loop*** runs up to (`end - begin + 1`) times per call giving a total of
	- `1 + 2 +... +(n-1) = n(n-1) / 2`
-  the ***recursive version*** has the same time complexity, since it performs identical operations
- ***best case***: when the array is already sorted, each `insertInOrder` exits immediately, making performance ***O(n)***
- the more sorted the data, the ***fewer shifts*** are needed, so insertion sort is efficient for ***small or mostly sorted arrays***
- ***space complexity***: o(1) since it **sorts in place**
- its often used in systems that make ***small updates to an already sorted dataset*** like customer or transaction lists

## Insertion Sort of a Chain of Linked Nodes

- **Insertion sort works naturally with linked structures**, since nodes can be **relinked** rather than moved or copied.
- The chain is divided into two parts:
    - **Sorted part** – starts with the first node.
    - **Unsorted part** – all remaining nodes.
- Each node from the unsorted part is **removed and inserted** into its correct position within the sorted part using the method `insertInOrder()`.
- **Insertion process:**
    - Traverse the chain using `currentNode` while keeping a `previousNode` reference.
    - Stop when the new node’s value is smaller than or equal to the current node’s data or when the end is reached.
    - Insert either **between nodes** (using both references) or at the **beginning** if it belongs before the first node.
- The method `insertionSort()` breaks the chain into sorted and unsorted parts by setting the first node’s link to `null`, then iteratively inserts each remaining node.
- If `unsortedPart = unsortedPart.getNextNode();` were moved **after** `insertInOrder(nodeToInsert)`, the code would fail—`nodeToInsert` would already be relinked, losing the reference to the next unsorted node.
- `insertionSort` is **non-static** because it acts on the **specific linked chain instance** referenced by `firstNode`.
- **Efficiency:** Like array insertion sort, this method is **O(n²)**, as `insertInOrder()` can make up to _n − 1_ comparisons per insertion, resulting in
    `1+2+...+(n-1) = n(n-1) / 2`
- Sorting linked nodes is harder to visualize and debug than arrays, but it avoids shifting elements—only **pointer adjustments** are needed.

## Shell Sort
- **Shell sort** (invented by Donald Shell in 1959) is a faster variation of **insertion sort** designed to handle **large, unsorted arrays** more efficiently.
- It improves speed by allowing entries to move **more than one position at a time**, fixing far-out-of-place elements early.
- The algorithm works by grouping elements that are a fixed **gap (or separation)** apart, sorting each group with an **insertion sort**, and then **reducing the gap** each pass until it becomes **1** (a final normal insertion sort).
- A common gap sequence halves the separation each pass: start with `n/2`, then `n/4`, and so on until `1`.
- Each pass makes the array **progressively more sorted**, so the final insertion sort finishes quickly.
- **Efficiency:** typically **O(n log² n)** (much faster than O(n²) insertion sort), though the exact time depends on the gap sequence used.
- **Space:** still **O(1)** (in-place).
- The **last gap = 1** ensures the entire array is completely sorted regardless of the earlier steps.

## The Shell Sort Algorithm
- **Shell sort** extends **insertion sort** by operating on entries that are **spaced apart** by a fixed gap (`space`).
- The key method, **`incrementalInsertionSort`**, performs an insertion sort on **every `space`-th element**, allowing values to move long distances in early passes.
- Each pass reduces the gap (`space`) — typically starting with `n / 2` and halving it until `space = 1`.
- When `space = 1`, the algorithm finishes with a standard insertion sort, fully ordering the array.
- The `shellSort` method repeatedly calls `incrementalInsertionSort` for each starting position (`begin`) up to `space - 1`.
- This approach makes the array **progressively more ordered**, improving performance dramatically over regular insertion sort.
- **Efficiency:** depends on gap sequence, but generally between **O(n log² n)** and **O(n^(3/2))**, much better than **O(n²)**.
- **Space:** O(1), since sorting is done in place
## The Efficiency of Shell Sort
- Though **Shell sort** performs multiple insertion sorts, it’s still **faster than O(n²)** because:
    - Early passes work on **smaller, widely spaced groups**,
    - Later passes work on arrays that are **increasingly sorted**, and
    - The **final pass** operates on an array that’s almost in order.
- The algorithm technically uses **three nested loops**, but its **worst case** is still **O(n²)**, not **O(n³)**.
- The **average case** (especially when _n_ is a power of 2) is about **O(n¹·⁵)**, making it much faster than insertion or selection sort for large arrays.
- **Optimization tip:**
    - When the gap (`space`) is **even**, some elements appear in the same groups across consecutive passes, causing **redundant comparisons**.
    - To fix this, add **1** to any even `space` value, ensuring that consecutive increments **share no common factors**.
    - This tweak improves the **worst case** to **O(n¹·⁵)**.
- With better gap sequences (like **Hibbard**, **Knuth**, or **Sedgewick** sequences), Shell sort can approach **O(n log² n)** performance.
- **Practical takeaway:** Shell sort offers a good balance of simplicity and speed, making it ideal for **moderately large arrays** where full advanced sorts (like merge or quicksort) may be unnecessary.

## Comparing the Sorting Algorithms
- **Selection sort** is the **slowest**, performing the same number of comparisons regardless of data order — always **O(n²)**.
- **Insertion sort** is faster when the array is **partially or mostly sorted**, with efficiency ranging from **O(n)** (best case) to **O(n²)** (worst case).
- **Shell sort** is the **fastest** of the three, improving on insertion sort by sorting distant elements first and reducing total movements.
- **Overall time complexities:**
- **Selection sort** always performs the same number of comparisons, so it’s consistently the **slowest**.
- ![[566b0302-5ea7-4502-9123-542a2188ca6c.png]]
- **Insertion sort** can be **very fast (O(n))** when data is already sorted but degrades to **O(n²)** otherwise.
- **Shell sort** improves insertion sort by allowing large element jumps early, achieving **O(n¹·⁵)** performance and being the **fastest overall** among the three.
- In practice:
    - Use **selection** only for small, simple datasets.
    - Use **insertion** when the list is **nearly sorted**.
    - Use **Shell** for **moderately large arrays** that need better efficiency without complex algorithms.