## Objectives

After studying this chapter, you should be able to:
- Implement the **ADT Queue** using a **linked chain** or an **array**.
- Add or remove nodes at either end of a **doubly linked chain**.
- Implement the **ADT Deque** using a doubly linked chain.
- Implement the **ADT Priority Queue** using either an array or a linked chain
## Implementing the ADT Queue

### 1. Linked Implementation of a Queue
- Use a **chain of linked nodes**.
- Queue’s **front** is at the **head** of the chain.
- Queue’s **back** is at the **tail**.
- With both head and tail references:
    - Removing from the front = **O(1)**.
    - Adding to the back = **O(1)**.
- Without a tail reference → inserting at the back requires a full traversal (**inefficient**).
- Memory use: nodes allocated only when needed, deallocated when removed

### Array-Based Implementation of a Queue
- Store queue entries in an array.
- Two main strategies:
    
    **a. Circular Array**
    - Front and back wrap around the array.
    - Keep count of entries to distinguish full vs empty.
    **b. Circular Array with One Unused Element**
    - Reserve one spot to tell the difference between full and empty states.
    - More efficient to test conditions.
- Time complexity: all queue operations are **O(1)**, except when resizing array.
    

---

### 3. Circular Linked Queue
- **Two-part circular linked chain**
    - One part for active queue.
    - One part for unused nodes.
- Dequeue removes data but keeps the node in the “available pool.”
- Efficient memory reuse

## Java Class Library Support
- `AbstractQueue` class: base class for queue implementations.
- Provides partial implementation; subclasses must define core methods

## Implementing the ADT Deque
- Requires **doubly linked nodes**: each node references both `next` and `previous`.
- Efficient because:
    - `removeFront()` and `removeBack()` = **O(1)**.
    - `addFront()` and `addBack()` = **O(1)**.
        
- Example implementations:
    - Standard doubly linked chain (with head and tail).
    - **Circular doubly linked chain**
        - Each node points to both next and previous.
        - No null references; single external reference needed.
        - Makes navigation faster

## Implementing the ADT Priority Queue
- **Array-based implementation**:
    - Keep entries in **sorted order** by priority.
    - Highest-priority at **end of array** → easy to remove.
        
- **Linked implementation**:
    - Keep highest-priority at **front of chain**.
    - Removal = **O(1)**.

- **Trade-off**:
    - Insertion may require shifting/traversal (**O(n)**).
    - Removal of highest-priority is fast.
- Future improvement: **Heap-based implementation** (introduced in Chapter 24)

|Structure|Enqueue|Dequeue|GetFront|Space|
|---|---|---|---|---|
|**Linked Queue**|O(1)|O(1)|O(1)|Node per entry|
|**Array Queue**|O(1)*|O(1)|O(1)|Fixed size (resizing costly)|
|**Deque (DLL)**|O(1) front/back|O(1) front/back|O(1)|Node per entry|
|**Priority Queue (Array/Chain)**|O(n) insertion|O(1) removal|O(1)|Array or linked nodes|
- **Linked Queue** = uses head and tail references.
- **Circular Array** = array where back/front “wrap around.”
- **Circular Array with one unused element** = technique to distinguish full vs empty.
- **Circular Linked Chain** = linked structure with “active” part and “available” part.
- **Doubly Linked Chain** = nodes reference both next and previous.
- **Circular Doubly Linked Chain** = no nulls, one reference gives access to both ends.
- **AbstractQueue** = partial implementation base class in Java.
- **Priority Queue implementations**:
    - Array → keep highest priority at end.
    - Linked chain → highest priority at front.
    - Heap (future chapter) → more efficient.