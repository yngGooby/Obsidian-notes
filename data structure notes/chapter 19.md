## the problem
- **Searching** means looking for a specific item (the _target_) in a collection of items.
- Searching is a **common real-world and programming task** (like finding your name on a list).
- In programming, an **ADT list** (Abstract Data Type list) can be searched using a **`contains`** method.
- The **`contains` method** returns a **boolean** value — `true` if the target is found, `false` if not.
- How `contains` works depends on the **list’s implementation** — it could be stored as an **array** or as a **linked list**.
**Simplified Summary**  
Searching is the process of finding a specific item, or target, within a group of items. In programming, this is like checking if your name exists in a list using the `contains` method, which returns true or false. The way this search is done depends on whether the list’s data is stored in an array or linked nodes.

## searching the unsorted array
- **Sequential (linear) search** checks each element one by one until it finds the target or reaches the end.
- Works for **unsorted arrays**, since there’s no order to use for skipping elements.
- Can be implemented **iteratively (with loops)** or **recursively (with method calls)**.
- This section focuses on both methods and compares their **efficiency**.
- Even though earlier list implementations ignored the first array element, here the **entire array** is searched.
**Simplified Summary**  
A sequential search in an unsorted array goes through each element one at a time until it finds the target or finishes the list. It can be done using loops or recursion, and the efficiency of both methods is analyzed. Unlike before, this search looks through every element in the array.

## An Iterative Sequential Search of an Unsorted Array
- **Iterative Sequential Search** checks each array element one at a time using a loop.
- The method `inArray` uses a **boolean variable `found`** and an **index counter** to track progress.
- The loop continues as long as the target hasn’t been found (`!found`) and the end of the array hasn’t been reached.
- If a match is found (`anEntry.equals(anArray[index])`), `found` becomes true and the loop stops immediately.
- If the loop finishes without finding a match, `found` stays false, meaning the target isn’t in the array.
- The search stops early when a match is found—**it doesn’t check unnecessary elements.**
- The diagram shows both **successful** and **unsuccessful** searches step-by-step.
- Question 1 extends this logic to return the **index position** of the match or `-1` if not found.
- Question 2 asks to implement the same idea using **ADT list operations** instead of direct array access.
**Simplified Summary**  
This section explains how an iterative sequential search works: it loops through each array element until it finds a match or reaches the end. If the target is found, the loop stops and returns true; if not, it returns false. The concept can be modified to return the index instead or to work with ADT list structures.

## A Recursive Sequential Search of an Unsorted Array
- A **recursive sequential search** checks the first element of an array; if it’s not the target, it searches the rest of the array.
- Each recursive call examines a **smaller subarray**, creating a self-reducing problem until the array becomes empty (the **base case**).
- The **base case** occurs when there are no elements left — the array is empty, so the method returns `false`.
- If the first element matches the target, the method returns `true`.
- Otherwise, the method calls itself again, shifting the search to the next index (`first + 1`).
- The main method (`inArray`) simplifies things for the client by calling a **private helper method** `search`, which takes `first` and `last` parameters to define the current search range.
- Each comparison in the recursive process checks the current element, then moves to the next until a match is found or all elements are checked.
**Simplified Summary**  
A recursive sequential search starts by checking the first element; if it doesn’t match, it searches the smaller part of the array. This continues until the element is found or the array is empty (base case). The helper method `search` handles the recursion using `first` and `last` parameters, while `inArray` simply starts the process. Each step compares one element, then moves forward if no match is found.

## The Efficiency of a Sequential Search of an Array
- Both **iterative and recursive** sequential searches make the same number of comparisons.
- **Best case (O(1))**: the target is found on the first comparison.
- **Worst case (O(n))**: the search checks every element — either the target is last or not present.
- **Average case (O(n/2))**, which simplifies to **O(n)**, since on average half the elements are checked.
- The time efficiency depends entirely on **where the target is located** (or if it’s missing).
**Simplified Summary**  
Sequential search takes the same time whether done with loops or recursion. If the target is first, it’s very fast (O(1)), but if it’s last or missing, it’s slow (O(n)). On average, about half the elements are checked, so the efficiency is still considered O(n).

## Searching a Sorted Array
- **Sequential search** is simple and easy to implement.
- It works well for **small arrays**, where the number of entries is low.
- As the number of entries grows, the search becomes **increasingly slow and inefficient**.
- The analogy of searching for a specific coin shows how time-consuming sequential search becomes with large datasets.
- This introduces the need for **faster search algorithms**.
**Simplified Summary**  
Sequential search is simple and fine for small arrays, but it becomes too slow as the data grows. Like searching through a huge jar of coins, it takes too long when there are many items, so faster methods are needed.

## A Sequential Search of a Sorted Array
- Sorting data (like coins by date) can make a **sequential search more efficient**.
- In a **sorted array**, if the search passes the point where the target should appear, it can **stop early**—there’s no need to check the rest.
- For example, when searching for 1999 in a sorted list that reaches 2000, you can stop because higher values follow.
- In contrast, an **unsorted array** requires checking every element to be sure.
- A **modified sequential search** for sorted data reduces unnecessary comparisons.
- Sorting first also allows the use of **even faster search algorithms**, which are introduced next.
**Simplified Summary**  
When data is sorted, a sequential search can stop early once it passes where the target should be, saving time. Unlike searching an unsorted list, you don’t need to check everything, and sorting also makes faster search methods possible.

## A Binary Search of a Sorted Array
- **Binary search** is used on **sorted arrays** and repeatedly divides the search range in half.
- It uses the **`compareTo`** method (from the `Comparable` interface) instead of just `equals` to determine if the target is **less than**, **equal to**, or **greater than** the middle element.
- The **base case** occurs when `first > last`, meaning there are no elements left to search.
- If the target equals the middle element, it’s found; if it’s smaller, the search continues in the **left half**; if it’s larger, it continues in the **right half**.
- Using `compareTo` requires the class to **implement `Comparable`**, and the `equals` method should match the logic used in `compareTo` to ensure consistency.
- The formula `mid = first + (last - first) / 2` avoids potential integer overflow compared to `(first + last) / 2`.
- Modifications:
    - To return the **index**, not just `true/false`, adjust the method to return `mid` or `-1`.
    - For **descending order arrays**, reverse the direction of comparisons:
        - If `desiredItem.compareTo(anArray[mid]) > 0`, search the **left half**, and if `< 0`, search the **right half**.
**Simplified Summary**  
Binary search works by repeatedly halving a sorted array and comparing the target to the middle value using `compareTo`. It’s faster than sequential search and depends on the array being sorted. The method stops when the target is found or when no elements remain. To adapt it, you can return the element’s index or flip the comparison logic for descending arrays.

## Java Class Library: The Method binarySearch
- `Arrays.binarySearch` searches a **sorted array** for a target value.
- Returns the **index** if found; otherwise, returns `-(insertIndex) - 1`.
- Works for **objects and primitive types**, but both types must match.
**Simplified Summary**  
`Arrays.binarySearch` finds an item’s index in a sorted array or tells where it should go if it’s missing.

## The Efficiency of a Binary Search of an Array
- **Binary search efficiency:** each comparison eliminates **half** of the remaining elements, making it extremely fast.
- The **number of divisions (k)** equals **log₂n**, representing how many times the array can be halved until one element remains.
- Each recursive call makes at most **two comparisons**, so total comparisons are roughly **2 × log₂n**.
- **Worst case:** O(log n); **Best case:** O(1); **Average case:** O(log n).
- Example: searching 1,000 items takes about **10 comparisons** instead of up to 1,000 in a sequential search.
- **Ceiling and floor**: rounding up or down helps express cases when n isn’t a perfect power of 2.
- The **recurrence relation** t(n) = 1 + t(n/2) also proves binary search’s logarithmic time complexity.
**Simplified Summary**  
Binary search halves the search space each step, giving it O(log n) efficiency. It only needs about 10 checks for 1,000 items, while sequential search might need 500–1,000. In the best case, it’s instant (O(1)); in the worst, it still grows slowly because each step removes half the data.

## Searching an Unsorted Chain
- In a **linked list**, searching is done by moving **node by node** through the chain.
- The **`contains`** method in a linked implementation performs a **sequential search**.
- Since nodes are connected by links, **accessing elements is slower** than with arrays, but the overall **efficiency (O(n))** is the same.
- The search can be implemented **iteratively or recursively**, just like with arrays.
- **Sequential search** is the **only practical option** for unsorted linked lists.
**Simplified Summary**  
Searching a linked list means checking each node one by one from the start until the target is found or the list ends. It works the same way as in arrays—either with loops or recursion—but takes longer to move between elements.

## An Iterative Sequential Search of an Unsorted Chain
- In a **linked list**, each node links to the **next node** using a reference.
- The **`firstNode`** variable always points to the start of the list and **should not be modified** during a search.
- A **local variable `currentNode`** is used to move through the chain without altering the list structure.
- The method uses a **while loop** to check each node’s data against the target.
- The search stops when the target is found (`found = true`) or when there are **no more nodes** (`currentNode == null`).
- This approach mirrors the **sequential search logic** used in arrays but applied to linked nodes.
**Simplified Summary**  
The linked list search uses a local variable to move through each node so the original list isn’t changed. It checks each node’s data until the target is found or the list ends, working just like a sequential array search.

## A Recursive Sequential Search of an Unsorted Chain
- A **recursive search** in a linked list checks the **first node**, and if it’s not the target, it recursively searches the **rest of the chain**.
- Unlike iterative search, recursion can’t use a **local `currentNode`** variable because it resets each call; instead, `currentNode` must be a **parameter** passed into the recursive method.
- The **private helper method `search`** handles recursion, checking one node per call until it either finds the target or reaches the end (`currentNode == null`).
- The **public `contains`** method starts the process by calling `search(firstNode, anEntry)`.
- This structure keeps implementation details hidden while preserving the same search logic used in arrays and other list types.
**Simplified Summary**  
The recursive search in a linked list checks one node at a time using a helper method that takes the current node as a parameter. The public `contains` method starts the search from the first node, and the recursion continues until the target is found or the list ends.

## The Efficiency of a Sequential Search of a Chain
- The **efficiency of sequential search** in a linked list is the same as in an array.
- **Best case:** the item is the first node → **O(1)**.
- **Worst case:** the entire chain is searched → **O(n)**.
- **Average case:** about half the nodes are checked → **O(n/2)**, which simplifies to **O(n)**.
**Simplified Summary**  
A sequential search in a linked list is just as efficient as in an array—instant if the target is first (O(1)), slow if it’s last or missing (O(n)), and on average still O(n).

## A Sequential Search of a Sorted Chain
- When a **linked list is sorted**, searching can **stop early** once a node’s value passes the target.
- The method uses **`compareTo`** to compare the target with each node’s data.
- The **while loop** continues only while the target is **greater** than the current node’s data.
- After traversal, a **final equality check** confirms whether the target was found.
- Because the list is sorted, **unsuccessful searches** end sooner than in unsorted chains, improving efficiency.
**Simplified Summary**  
In a sorted linked list, the search moves through nodes until it finds a match or passes where the item should be, ending early if it’s not found—making it faster than searching an unsorted list.

## A Binary Search of a Sorted Chain
- In an **array**, finding the middle element is easy because elements are accessed directly using indices.
- In a **linked list**, there are **no indices**, so reaching the middle node requires **traversing from the start**, which takes extra time.
- Performing a binary search on a linked list means repeatedly finding the middle node, which is **inefficient** because it requires multiple traversals.
- Even though the data may be sorted, the **node-by-node access** makes binary search **impractical** on linked structures.
**Simplified Summary**  
Binary search works great on arrays but not on linked lists because finding the middle node requires walking through the list each time, making it slower than a simple sequential search.
## Choosing a Search Method
- **Sequential search:** works on any data (sorted or unsorted) and only requires the **`equals`** method to compare objects.
- **Binary search:** requires data to be **sorted** and objects to implement **`compareTo`** from the `Comparable` interface.
- If the array is **small** or **unsorted**, use **sequential search** — sorting it first isn’t worth the time.
- If the array is **large and sorted**, **binary search** is far faster.
- **Efficiency summary:**
    - Sequential search — **O(1)** best, **O(n)** average/worst.
    - Binary search — **O(1)** best, **O(log n)** average/worst.
- **Iterative vs recursive:**
    - Recursive sequential search uses extra space, so **iteration is more efficient** for it.
    - Binary search recursion is **efficient and easier to code**, with minimal overhead.
**Simplified Summary**  
Use sequential search for small or unsorted data and binary search for large, sorted arrays. Sequential needs `equals`, while binary needs `compareTo`. Recursion works well for binary search, but iteration is better for sequential since it saves space.