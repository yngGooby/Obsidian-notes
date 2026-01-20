
## merge sort
- **Core Idea:** Merge sort uses a _divide and conquer_ approach — it splits an array into halves, sorts each half, and merges them into one sorted array.
- **Divide and Conquer Concept:**
    - The problem is _divided_ into smaller, distinct subproblems.
    - Each subproblem is _conquered_ (solved) individually.
    - Their solutions are _combined_ to solve the original problem.
- **Recursion:**
    - Merge sort is typically expressed _recursively_.
    - A recursive algorithm defines the solution in terms of _smaller versions_ of the same problem.
    - However, recursion is _not required_ for divide and conquer algorithms.
- **Comparison Example:**
    - The recursive _selection sort_ (from the previous chapter) reduces the problem size but _does not divide_ it into two separate sorting tasks.
    - Merge sort _does_ divide the problem, making it a true divide and conquer method.
- **Merge Step:**
    - The **merge phase** is the most important and programming-intensive part of the algorithm.
    - It handles the actual process of combining two sorted subarrays into one sorted array.
## merging arrays
- **Core Idea:** Merging two **sorted arrays** into one sorted array is straightforward but requires creating a **third array** to hold the result.
- **Process:**
    - Start from the **beginning of both arrays**.
    - Compare the **current elements** from each array.
    - **Copy the smaller element** into the new third array.
    - Move forward in the array that contributed the smaller element.
- **When One Array Ends:**
    - Once all elements from one array have been copied,
    - **Copy the remaining elements** from the other array directly into the new array.
- **Result:** The new array contains all elements from both arrays in **ascending order**.
**In short:** Merging sorted arrays works by repeatedly taking the smaller element from two input arrays and placing it into a new array until both are fully combined in order.
## recursive merge sort
- Core idea: Merge sort is a divide and conquer algorithm that recursively splits an array into halves, sorts each half, and merges them into one sorted array.
- Process:
    - Divide the array into two halves using a midpoint.
    - Recursively sort each half.
    - Merge the two sorted halves into a temporary array.
    - Copy the merged results back to the original array.
- Merge step:
    - Compare the first elements of both halves.
    - Copy the smaller element into the temporary array.
    - Continue until one subarray is empty.
    - Copy all remaining elements from the other subarray.
    - This step performs the actual sorting.
- Recursive flow:
    - The array is divided until each part contains a single element.
    - Merging begins from the smallest parts up to the full array.
    - Sorting happens during merging, not during splitting.
- Efficiency notes
    - The merge step does most of the work.
    - The temporary array should only be created once for efficiency.
    - Merge sort rearranges elements during merging, not recursion.
    - Time complexity is O(n log n).
- In short: Merge sort splits an array into smaller sections, recursively sorts them, and merges them back together, with the merging phase performing all the sorting work.

## Efficiency of merge sort
- Core idea: Merge sort’s efficiency comes from repeatedly dividing the array in half, sorting, and merging, leading to a total of **log₂n levels** of recursive calls and **O(n)** work per level.
- Recursive levels:
    - Each time the array is split, the number of subarrays doubles while their size halves.
    - If n = 2ᵏ, then there are **k levels of recursion** (e.g., n = 8 → 3 levels).
- Merge operations:
    - Each merge involves up to **n – 1 comparisons** and about **2n moves** (to and from the temporary array).
    - Therefore, each merge step is **O(n)** regardless of array order.
- Total work:
    - Every level performs **O(n)** work, and there are **log₂n** levels.
    - Thus, total efficiency = **O(n log n)** for **worst**, **best**, and **average** cases.
- Space requirement:
    - Merge sort needs a **temporary array** for merging, which increases memory use compared to in-place algorithms.
    - This is its main **disadvantage** despite its strong time performance.
- Recurrence relation:
    - Expressed as **t(n) = 2t(n/2) + n**, showing that the algorithm splits the problem in two and performs linear merging each time.
    - Solving this gives **t(n) = n log₂n**, confirming the **O(n log n)** time complexity.
- In short: Merge sort performs **log₂n levels of O(n)** work, achieving consistent **O(n log n)** time in all cases but requires extra space for merging
## iterative merge sort
- Core idea: Iterative merge sort removes recursion and uses loops to control merging, making it more efficient in **time and space** since it avoids recursive calls and stack usage.
- Recursive vs. iterative:
    - Recursive merge sort relies on recursive calls to manage division and merging.
    - Iterative merge sort must **manually control** the merging process using loops.
- Process:
    - Begin by merging pairs of **single elements** into sorted two-element subarrays.
    - Then merge pairs of **two-entry subarrays** into sorted four-entry subarrays.
    - Continue doubling the subarray size each pass until the entire array is sorted.
- Leftover entries:
    - If an odd number of subarrays remain after a merge pass, the last group must be merged carefully with the remaining entries.
- Advantages:
    - **Eliminates recursive overhead**, making it more memory-efficient.
    - Can save time by reducing unnecessary copying between arrays during merges.
- In short: Iterative merge sort uses loops to merge progressively larger sorted subarrays, avoiding recursion and stack use while maintaining merge sort’s efficiency.
## merge sort in java class library
- Core idea: Iterative merge sort removes recursion and uses loops to handle merging, making it faster and more memory-efficient since it doesn’t create activation records on the call stack.
- Process:
    - Start at the beginning of the array, merging pairs of single elements into sorted two-element subarrays.
    - Repeat the process, merging pairs of two-entry subarrays into four-entry subarrays, and continue doubling until the array is sorted.
    - Handle any leftover elements carefully if the array can’t be evenly divided.
- Advantage:
    - Saves both time and space by eliminating recursive calls and reducing unnecessary copying between arrays during merges.
    - However, it’s trickier to implement correctly compared to the recursive version.
- Merge sort in Java:
    - The `Arrays` class in `java.util` uses a **merge sort** for sorting arrays of objects that implement the `Comparable` interface.
    - It optimizes performance by skipping the merge step when the left half’s largest element is not greater than the right half’s smallest.
- Stable sorting:
    - A sorting algorithm is **stable** if it keeps equal elements in their original order (e.g., two people with the same age stay alphabetically ordered after sorting by age).
    - The merge sorts in Java are **stable**, making them useful for multi-level sorting like sorting first by name, then by age.
- In short: Iterative merge sort improves efficiency by removing recursion, and Java’s built-in merge sort adds optimizations and stability to preserve order among equal elements.

## quick sort
- Core idea: Quick sort is another **divide and conquer** algorithm that sorts an array by selecting a **pivot element** and dividing the array into two parts based on it.
- Process:
    - Choose one element as the **pivot**.
    - Rearrange the array so that:
        - All elements **before the pivot** are less than or equal to it.
        - All elements **after the pivot** are greater than or equal to it.
    - This rearrangement is called **partitioning**.
- After partitioning:
    - The pivot is in its **final sorted position**.
    - Two subarrays are formed: **Smaller** (values ≤ pivot) and **Larger** (values ≥ pivot).
    - Recursively apply quick sort to both subarrays.
- Key difference from merge sort:
    - Merge sort always splits arrays in half, while quick sort splits them based on the pivot’s position.
- In short: Quick sort sorts an array by picking a pivot, partitioning elements around it, and recursively sorting the left and right sections, placing the pivot in its correct position each time.

## The Efficiency of Quick Sort
- Core idea: Quick sort’s efficiency depends on how evenly the pivot divides the array, with most of the work done during the **partitioning phase** before the recursive calls.
- Partitioning:
    - Requires at most **n comparisons**, making it an **O(n)** operation.
    - The pivot determines how balanced the two resulting subarrays are.
- Best case:
    - Occurs when the pivot divides the array into **two equal halves**.
    - Recursive calls then halve the array each time, resulting in **O(n log n)** performance—similar to merge sort.
- Worst case:
    - Happens when the pivot produces **one empty subarray**, leaving all other elements in the other subarray.
    - This leads to **n levels of recursion**, making the algorithm **O(n²)**.
- Average case:
    - On average, quick sort performs **O(n log n)**.
    - Despite its worst-case potential, it is often **faster than merge sort** in practice because it doesn’t require extra memory for a temporary array.
- Pivot selection:
    - The efficiency depends on how the pivot is chosen.
    - Poor pivot selection (like always choosing the first element in a sorted list) can cause **worst-case behavior**.
    - A good selection method helps avoid inefficiency on sorted or nearly sorted arrays.
- In short: Quick sort averages **O(n log n)** efficiency but can degrade to **O(n²)** if partitions are uneven; its speed and low memory use make it powerful when pivots are well-chosen.

## Creating the Partition
- Core idea: Quick sort divides an array around a chosen **pivot**, rearranging elements so smaller values go to the left, larger ones go to the right, and the pivot ends up in its correct sorted position.
- Partitioning process:
    - Choose a pivot and temporarily **swap it with the last entry** to move it out of the way.
    - From the **left**, find the first element greater than or equal to the pivot.
    - From the **right**, find the first element less than or equal to the pivot.
    - If the left index is still before the right, **swap those two entries** and continue searching inward.
    - When the search indices cross, **swap the pivot** back into its final position between the two subarrays.
- Handling equal entries:
    - Entries equal to the pivot can end up in either subarray.
    - Allowing equal values to appear on both sides helps keep the subarrays more balanced and improves efficiency.
- Pivot selection:
    - Ideally, the pivot should be the **median** value so the array splits evenly, but finding the true median is inefficient.
    - Instead, use the **median-of-three** method — choose the median of the **first**, **middle**, and **last** elements as the pivot.
    - This approach avoids worst-case performance when the array is already sorted or nearly sorted.
- Adjusting the partition algorithm:
    - After sorting the first, middle, and last entries, the **largest (last)** belongs in the right subarray and can remain in place.
    - Swap the pivot with the **next-to-last** entry instead of the last to start the partition.
    - The left search begins at **first + 1**, and the right search begins at **last − 2**.
    - This ensures the searches never go beyond the array’s bounds.
- Key property:
    - Quick sort **rearranges entries in place**, and each partition step puts one element (the pivot) in its **final sorted position**, leaving the rest divided into smaller unsorted sections.
- In short: Quick sort’s partition process swaps elements around a pivot, balancing efficiency by allowing equal entries on either side and improving performance through the median-of-three pivot method.
## Implementing Quick Sort
- Core idea: Implementing quick sort involves three main parts — **pivot selection**, **partitioning**, and the **main quick sort method** — all working together to efficiently sort an array.
- Pivot selection:
    - Uses **median-of-three** (first, middle, last) to find a balanced pivot.
    - Sorting these three ensures the **middle element** becomes the pivot.
    - Helps avoid worst-case behavior for sorted or nearly sorted arrays.
- Partitioning:
    - Assumes at least four elements.
    - After sorting the first, middle, and last entries:
        - The pivot (middle value) is swapped with the **next-to-last entry** to move it aside.
        - Left index starts at **first + 1**, right index at **last − 2**.
    - From the left, skip entries **less than** the pivot.
    - From the right, skip entries **greater than** the pivot.
    - When left < right, **swap** those two entries.
    - When left ≥ right, stop and **swap the pivot** into its final position between the two subarrays.
    - The pivot’s position divides the array into **Smaller** (≤ pivot) and **Larger** (≥ pivot) subarrays.
- Quick sort method:
    - For arrays smaller than **MIN_SIZE** (like 10 or fewer elements), use **insertion sort** instead of recursion for efficiency.
    - Otherwise, call **partition()** to divide the array, then recursively apply quick sort to the two resulting sections.
    - This hybrid approach improves performance on small arrays and reduces overhead.
- Example (sorting 9 6 2 4 8 7 5 3 with MIN_SIZE = 4):
    1. First, middle, and last entries (9, 8, 3) → sorted as 3, 8, 9 → pivot = 8.
    2. Partition places 8 in its correct position, producing two subarrays: [6 2 4 7 5 3] and [9].
    3. Recursively apply quick sort to [6 2 4 7 5 3]; pivot = median of (6, 4, 3) → 4.
    4. Partition again → pivot 4 placed correctly → [2 3] | 4 | [7 5 6].
    5. Arrays smaller than MIN_SIZE use insertion sort.
    6. Final sorted array: [2 3 4 5 6 7 8 9].
- In short: Quick sort selects a balanced pivot using median-of-three, partitions the array around it, recursively sorts both sides, and switches to insertion sort for small arrays to maximize efficiency.

## Quick Sort in the Java Class Library
- Core idea: Quick sort has three main parts — pivot selection, partitioning, and the main quick sort method.
- Pivot selection:
    - Uses the median-of-three (first, middle, last) entries to find a balanced pivot.
    - Makes the middle element the pivot to avoid worst-case cases in sorted arrays.
- Partitioning:
    - Swaps the pivot with the next-to-last entry to move it aside.
    - Left index starts at first + 1; right index starts at last − 2.
    - Moves left index past smaller values and right index past larger ones.
    - Swaps entries when left < right, and when left ≥ right, swaps the pivot into place.
    - Divides the array into Smaller (≤ pivot) and Larger (≥ pivot).
- Quick sort method:
    - Uses insertion sort for small arrays under MIN_SIZE for efficiency.
    - Otherwise, partitions and recursively sorts both sides.
- Example: Sorting 9 6 2 4 8 7 5 3 results in [2 3 4 5 6 7 8 9].
- In short: Quick sort finds a balanced pivot, partitions around it, recursively sorts both sides, and switches to insertion sort for small arrays to boost performance.

## Radix sort
- Core idea: Radix sort is a **non-comparison** sorting algorithm that works on data with **fixed-length strings or numbers**.
- Process:
    - Each entry is treated as a string of equal length (e.g., 003, 019, 123).
    - Sort by **digit position**, starting from the **rightmost digit** and moving left.
    - Use **10 buckets (0–9)** to group numbers by digit value, keeping their order.
    - After each pass, collect numbers back into the array and repeat for the next digit.
- Example:
    - Rightmost digit → middle digit → leftmost digit.
    - Final sorted order: 003 019 123 129 210 220 294 398 513 528.
- Efficiency:
    - Runs in **O(n)** for fixed-length data, faster than comparison sorts.
    - Not suitable for general-purpose sorting because it only works with data of **uniform length**.
- Aside:
    - Inspired by **punched card sorters**, where cards were grouped by column holes into bins, similar to radix sort buckets.

## Efficiency of radix sort
- Core idea: Radix sort’s efficiency depends on both the **number of items (n)** and the **number of digits (d)** per item
- Efficiency:
    - The inner loop runs **n times**, and the outer loop runs **d times**, giving a time complexity of **O(d × n)**.
    - Since integers have a fixed number of digits (around 10), **d is constant**, making radix sort effectively **O(n)**.
- Limitation:
    - Radix sort is efficient only when **d is small and fixed** compared to n; it’s not suitable for all data types.
- For words instead of numbers:
    - You would need **26 buckets** (one for each letter of the alphabet).
    - The algorithm would group and sort based on **characters** instead of digits.
    - Each pass would process a different **letter position** (e.g., last letter to first).
## comparing algorithms 
- Core idea: Different sorting algorithms vary in efficiency depending on data size and type, with **radix, merge, and quick sort** generally performing best.
- Efficiency summary (Big O):
    - **Radix sort:** O(n) in all cases but limited to specific data.
    - **Merge sort:** O(n log n) consistently.
    - **Quick sort:** O(n log n) average/best, O(n²) worst.
    - **Shell sort:** Between O(n¹·⁵) and O(n²).
    - **Insertion and selection sort:** O(n²) in all cases.
- Comparison by size:
    - For **small arrays (n ≤ 100)** or **nearly sorted data**, **insertion sort** is efficient.
    - For **large arrays**, **quick sort** outperforms Shell and insertion sorts.
    - **Merge sort** is best when sorting data stored externally (e.g., on disk).
- In short: Radix sort is fastest when applicable, while quick sort is generally the most efficient and practical for large in-memory data sets.

