

# DS&A Quiz Sheet — Chapters 6–8

## Chapter 6 — Stacks (ADT, usage, implementations)

**Core ADT (LIFO):** `push(T)`, `pop():T` (throw if empty), `peek():T` (throw if empty), `isEmpty()`, `clear()`.  
**Access rule:** only the **top** is directly accessible.

**Expression problems**

- **Balanced delimiters:** push lefts; on right, must match top; empty at end.
    
- **Infix → Postfix (outline):** output operands; push operators by precedence/associativity; pop to output on lower precedence or on `)`.
    
- **Postfix eval:** scan L→R; push operands; operator pops 2, computes, pushes result.
    
- **Infix eval:** use **two stacks** (operators + operands).
    

**Program runtime stack**

- **Activation record / frame** pushed on **method call** (args, locals, return address); popped on **return**.
    
- Program counter points to current instruction; GC reclaims unreachable frames/objects automatically.
    

**Implementations & where “top” lives**

- **Linked stack:** top = **head node**; `push`/`pop` O(1); pointer overhead.
    
- **Array/Vector stack:** top = **last occupied index**; `push`/`pop` O(1) (amortized for array); occasional resize; great locality.
    

**Mini ASCII**
Linked (top=head): top -> [data|next] -> [ ] -> null
Array (top=end):   [bottom ...        top]

## Chapter 7 — Queues, Deques, Priority Queues (ADTs + Java behavior)

### Queue (FIFO)

- **Rule:** add at **back**, remove from **front**; only **front** directly retrievable.
    
- **ADT:** `enqueue(T)`, `dequeue():T` (throw if empty), `getFront():T` (throw if empty), `isEmpty()`, `clear()`.
    

**Java Queue quick table (public method behavior)**

|Enqueue|Dequeue|Peek|
|---|---|---|
|`add` → **throws** on failure|`remove` → **throws** if empty|`element` → **throws** if empty|
|`offer` → returns **false**|`poll` → returns **null**|`peek` → returns **null**|
**Problem-Solved patterns you must recognize**

- **Waiting-line simulation:** time-driven loop; random arrivals & service times; at end report **served count**, **total wait**, **avg wait**, **left in line** (Poisson arrivals common).
    
- **Capital gain (FIFO):** sell shares in **purchase order** using a queue of lots (handle partial lots).
    

---

### Deque (double-ended queue)

- **Idea:** acts like queue **and** stack; both ends supported.
    
- **Ops pairs (throw vs non-throw)**
    
    - Add: `addFirst/offerFirst`, `addLast/offerLast`
        
    - Remove: `removeFirst/pollFirst`, `removeLast/pollLast`
        
    - Peek: `getFirst/peekFirst`, `getLast/peekLast`
        
- **Stack ops on Deque:** `push(T)` adds to **front**, `pop()` removes **front**.
    

**ArrayDeque (modern choice)**

- Default initial capacity **16**; auto-grows.
    
- Prefer over legacy `Stack` for stack behavior.

### Priority Queue (by priority, not arrival)

- **Rule:** highest priority removed first (Java `PriorityQueue` = **min-priority** by **natural order** unless given a `Comparator`; **no `null`** elements).
    
- **Common ops (mirror Queue semantics):**
    
    - Insert: `add/offer`
        
    - Remove highest: `remove/poll`
        
    - Peek highest: `element/peek`
        
- **Default capacity:** **11**; auto-grows.

## Chapter 8 — Implementations (how to build them + costs)

### Queue implementations

**Linked queue (singly linked, head/tail)**

- Keep **front=head**, **back=tail**.
    
- `enqueue` O(1): attach after tail; move tail.
    
- `dequeue` O(1): read head; move head; if empty, set tail null.
    

**Array queue (circular)**

- Keep `front`, `back` and use `(i+1) % capacity`.
    
- **Two strategies:**
    
    1. **Count** entries: empty if `count==0`, full if `count==capacity`.
        
    2. **One unused slot**: empty if `front==back`, full if `(back+1)%cap==front`.
        
- Resizing: copy in logical order starting at 0; amortized O(1) enqueue.
    

**Two-part circular linked queue (node pool)**

- Split ring into **active** and **available** nodes; `dequeue` returns node to pool → fewer allocations under load.


### Deque implementation

**Doubly linked list (DLL)**

- Nodes have `prev/next`; external `first/last` refs (or circular DLL to avoid nulls).
    
- `add/remove` at **front/back** are all **O(1)**; `getFirst/getLast` O(1).
    

### Priority queue implementations (pre-heap trade-offs)

- **Array sorted:** insert O(n), remove-highest O(1).
    
- **Array unsorted:** insert O(1), remove-highest O(n).
    
- **Linked sorted:** insert O(n), remove-highest O(1).
    
- **Linked unsorted:** insert O(1), remove-highest O(n).
    
- **Heaps (later):** insert/remove ~ **O(log n)**, peek O(1) — best balanced choice.

Complexity quick tables
![[Pasted image 20250923192533.png]]
## Quiz-bait checklist (run this before every quiz)

- Know **where top/front/back live** in each impl.
    
- Can label **which methods throw** vs **return `null/false`** (`Queue`/`Deque`).
    
- Recall **ArrayDeque=16**, **PriorityQueue=11** defaults; both auto-grow.
    
- Explain **why PQ removes smallest by default** in Java and how to change it (Comparator).
    
- Simulate **waiting line stats** + compute **FIFO stock gain** on a tiny example.
    

Want me to convert this into printable PDF or flashcards next?