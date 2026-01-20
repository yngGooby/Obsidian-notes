## What Is Recursion?
- This section introduces **recursion**, a process where a problem is solved by breaking it into smaller, identical subproblems.
- Like a contractor hiring subcontractors, each recursive call handles a smaller version of the same task until reaching a **base case**—a problem small enough to solve directly.
- Example: a **countdown** from 10—each person (or method call) counts one number and asks the next to continue until reaching 1, then signals completion back up the chain.
- In Java, recursion is when a **method calls itself**, such as:
    
    ```java
    public static void countDown(int integer) {
        System.out.println(integer);
        if (integer > 1)
            countDown(integer - 1);
    }
    ```
    
    Here, the base case is when `integer` equals 1.
- When designing recursion, identify:
    1. The **direct contribution** to the solution.
    2. The **smaller, identical problem** to solve next.
    3. The **base case** where recursion stops.
- **Design guidelines:**
    - Include an input parameter.
    - Use an `if` or `switch` to distinguish cases.
    - Define at least one **base case** that ends recursion.
    - Ensure recursive calls move closer to the base case.
- **Infinite recursion** occurs if no base case is checked or reached.
- Recursive methods can often be rewritten **iteratively** using loops; recursion uses self-calls, iteration uses repetition.
##### **Core Concepts**
- **Recursion:** A method calling itself to solve smaller versions of a problem.
- **Base Case:** The simplest case that stops recursion.
- **Recursive Call:** The self-invocation that solves a smaller subproblem.
- **Infinite Recursion:** Happens when no base case is reached.
- **Iteration vs. Recursion:** Loops repeat; recursion re-invokes the same method.
##### **Simplified Notes**
- Recursion solves problems by dividing them into smaller, identical parts.
- Always include a **base case** to stop recursion.
- Each recursive call works on a **smaller input**.
- Recursion and iteration often achieve the same result but in different ways.
- **Note simplified:** Recursion is a method calling itself until reaching a simple, solvable case.
##  Tracing a Recursive Method
- This section traces how the recursive **countDown** method actually executes when called.
- Example: calling `countDown(3)` prints **3**, then calls `countDown(2)`, which prints **2**, then calls `countDown(1)`, which prints **1** and stops.
- Each recursive call **pauses** the current one until it finishes, then resumes in reverse order when returning.
- Java handles this using **activation records**—snapshots that store each method’s state (variables, parameters, current instruction).
- These records are stored in the **program stack**, which allows Java to pause and resume recursive calls properly.
- Each new recursive call pushes a new record on the stack; when it finishes, the record is popped off.
- Recursive methods use **more memory** than iterative ones because each call adds a new activation record.
- If recursion goes too deep or never ends, it can cause a **stack overflow** error.
##### **Core Concepts**
- **Activation Record:** A memory block storing the state of a method call.
- **Program Stack:** Manages active method calls; recursion pushes multiple records.
- **Stack Overflow:** Error caused by excessive or infinite recursion.
- **Return Sequence:** Each call completes in reverse order of its invocation.
##### **Simplified Notes**
- Recursive calls pause the current method and resume after finishing smaller ones.
- Each call adds a record to the stack, using extra memory.
- Too many recursive calls cause a stack overflow.
- **Note simplified:** Recursion works by stacking calls and returning them in reverse order.

## Recursive method that return a value
- This section introduces **valued recursive methods**, which return a result rather than just performing actions.
- Like void methods, valued recursive methods must include a **base case** and **recursive case**, but each case must also return a value.
- Example: computing the sum `1 + 2 + … + n` uses the recursive method `sumOf(n)`, where
    - **Base case:** if `n == 1`, return `1`.
    - **Recursive case:** return `sumOf(n - 1) + n`.
- Tracing `sumOf(3)` shows the order of calls and returns:
    - `sumOf(3)` → calls `sumOf(2)` → calls `sumOf(1)` → returns 1 → adds back up: `1 + 2 = 3`, then `3 + 3 = 6`.
- Recursive methods work correctly when designed with a clear **base case**, smaller recursive steps, and correct value returns.
- If recursion fails, review whether:
    - You have at least one base case,
    - Each recursive call gets closer to that base case, and
    - Each case correctly returns a value.
- While recursion can elegantly express logic, **large n values** may cause **stack overflow**, making iterative versions more efficient in simple problems.
##### **Core Concepts**
- **Valued Recursion:** Recursive methods that return a value.
- **Base Case:** The smallest solvable instance that stops recursion.
- **Recursive Case:** Defines the smaller problem and combines its result with a local contribution.
- **Debugging Rule:** Check for correct input handling, base cases, smaller recursive calls, and returned values.
- **Efficiency:** Iterative versions are safer for large problems due to lower memory use.
##### **Simplified Notes**
- Valued recursion works like void recursion but always returns a value.
- Every case—recursive or not—must produce a return.
- Example: `sumOf(n) = sumOf(n - 1) + n`, with base case `sumOf(1) = 1`.
- Trace shows recursive calls pause and resume in reverse order.
- **Note simplified:** Recursive methods are elegant but can overflow memory for large inputs, so use iteration when simpler.

## Recursively Processing an Array
- This section introduces how **recursion can process arrays**, preparing for future recursive searching and sorting algorithms.
- Example task: displaying all integers in an array recursively rather than iteratively.
- **Version 1 – Starting at the first element:**  
    Display `array[first]`, then recursively call `displayArray(array, first + 1, last)` until `first == last` (**base case**).  
    → Processes the array **forward**.
- **Version 2 – Starting at the last element:**  
    Recursively display the portion from `first` to `last − 1`, then display `array[last]`.  
    → Processes the array **backward** but gives the same output order.
- **Version 3 – Dividing the array in half:**  
    Split the array using `int mid = first + (last − first) / 2;`  
    Recursively display the **left half**, then the **right half**.  
    → Base case: a single element (`first == last`).
- **Alternative idea:** recursively display the left half, then the **middle element**, then the right half.
- When working with very large arrays, the safe midpoint formula `first + (last − first)/2` prevents **integer overflow**.
##### **Displaying a Bag Recursively**
- The **ArrayBag** class can use recursion to display its contents.
- `display()` (public) calls a private helper `displayArray(first, last)` that handles the recursive display.
    
    ```java
    public void display() {
        displayArray(0, numberOfEntries - 1);
    }
    private void displayArray(int first, int last) {
        System.out.println(bag[first]);
        if (first < last)
            displayArray(first + 1, last);
    }
    ```
    
- The recursive helper is **private** because it depends on the bag’s internal structure, which the client should not access.
##### **Core Concepts**
- **Recursive Array Processing:** Divide an array into smaller parts until a simple base case is reached.
- **Base Case:** A single element—display it directly.
- **Recursive Case:** Handle one element or half, then call recursively for the rest.
- **Private Helper Methods:** Used when recursion requires internal data (like `bag[]`).
- **Overflow Precaution:** Use `first + (last − first)/2` to find the midpoint safely.
##### **Simplified Notes**
- Arrays can be processed recursively from the start, the end, or by dividing in halves.
- Each recursive call works on a smaller section of the array.
- Recursive helper methods are private when they depend on a class’s internal data.
- **Note simplified:** Recursive array methods use smaller subarrays until one element remains; helper methods keep internal details hidden.
## Recursively Processing a Linked Chain
- This section shows how to **process linked chains recursively** using methods similar to those for arrays but adapted for nodes.
- In the **linked version of `display()`**, the method calls a **private helper** `displayChain(Node nodeOne)`.
    - **Base case:** when `nodeOne` is `null` (empty chain).
    - **Recursive case:** display the first node’s data, then call `displayChain(nodeOne.getNextNode())` to display the rest.
    - Example:
        
        ```java
        public void display() {
            displayChain(firstNode);
        }
        private void displayChain(Node nodeOne) {
            if (nodeOne != null) {
                System.out.println(nodeOne.getData());
                displayChain(nodeOne.getNextNode());
            }
        }
        ```
    → Processes the chain **forward**, node by node.
- To **display the chain backward**, recursion handles the order automatically by waiting until it reaches the end, then printing while returning:
    ```java
    public void displayBackward() {
        displayChainBackward(firstNode);
    }
    private void displayChainBackward(Node nodeOne) {
        if (nodeOne != null) {
            displayChainBackward(nodeOne.getNextNode());
            System.out.println(nodeOne.getData());
        }
    }
    ```
    - **Base case:** `nodeOne == null`.
    - **Recursive case:** first process the rest of the chain, then print the current node.
    - This reverses the order of output without using loops or extra storage.
##### **Core Concepts**
- **Recursive Chain Processing:** Uses the first node as the starting point and calls itself for the rest.
- **Base Case:** Stop when the node reference is `null` (end of chain).
- **Forward vs. Backward Traversal:**
    - Forward → process current node before recursion.
    - Backward → process current node **after** recursion.
- **Efficiency:** Recursion simplifies reverse traversal that would otherwise be tedious with iteration.
##### **Simplified Notes**
- Recursive methods can easily handle linked lists by processing one node at a time.
- Base case: stop when the node is `null`.
- Printing after the recursive call prints the list **backward**.
- **Note simplified:** Recursion is ideal for traversing linked chains forward or backward since it naturally handles each node one at a time.
## The Time Efficiency of Recursive Methods/countdowns
- This section explains how to measure the **time efficiency of recursive methods** using **recurrence relations**, which express a method’s runtime in terms of smaller versions of the same problem.
- Example:
    
    ```java
    public static void countDown(int n) {
        System.out.println(n);
        if (n > 1)
            countDown(n - 1);
    }
    ```
    - Base case → when `n == 1`, takes constant time → **t(1) = 1**.
    - Recursive case → one constant-time operation + time for a smaller problem → **t(n) = 1 + t(n − 1)**.
- Expanding this recurrence gives **t(n) = n**, since each recursive call adds one constant step.
- A **proof by induction** confirms that the relationship holds for all n ≥ 1.
- Therefore, the **countDown** method’s time complexity is **O(n)**, meaning it grows linearly with n.
##### **Core Concepts**
- **Recurrence Relation:** A formula expressing time t(n) in terms of smaller inputs (e.g., t(n) = 1 + t(n − 1)).
- **Base Case:** The smallest instance with a known solution (e.g., t(1) = 1).
- **Proof by Induction:** Confirms that the recurrence-derived formula works for all valid inputs.
- **Linear Growth:** If each call adds one step, total time equals the number of recursive calls → O(n).
##### **Simplified Notes**
- Recursive runtime is found by forming and solving a recurrence relation.
- `countDown(n)` takes **n constant steps**, so it’s **O(n)**.
- **Note simplified:** A recursive method’s time equals the number of calls it makes; `countDown` makes n calls → O(n).

## The Time Efficiency of Computing xn
- This section analyzes the **time efficiency of an improved recursive method** for computing xnx^nxn.
- The efficient approach reduces recursive calls by halving n each time:
    - If n is even: xn=(xn/2)2x^n = (x^{n/2})^2xn=(xn/2)2
    - If n is odd: xn=x(x(n−1)/2)2x^n = x \times (x^{(n-1)/2})^2xn=x×(x(n−1)/2)2
    - If n=0n = 0n=0: x0=1x^0 = 1x0=1
- Each call performs only constant-time multiplications (**O(1)**), so runtime depends entirely on the number of recursive calls.
- The recurrence relation describing its time is:
    - t(n)=1+t(n/2)t(n) = 1 + t(n/2)t(n)=1+t(n/2) for n≥2n ≥ 2n≥2
    - t(1)=1t(1) = 1t(1)=1, t(0)=1t(0) = 1t(0)=1
- Expanding this for n=16n = 16n=16:  
    t(16)=1+t(8)=2+t(4)=3+t(2)=4+t(1)t(16) = 1 + t(8) = 2 + t(4) = 3 + t(2) = 4 + t(1)t(16)=1+t(8)=2+t(4)=3+t(2)=4+t(1).  
    Since 16=2416 = 2^416=24, the number of recursive calls = **log₂(n)**, giving t(n)=1+log2(n)t(n) = 1 + log₂(n)t(n)=1+log2​(n).
- A proof by induction confirms this relationship, showing the method’s time complexity is **O(log n)**.
##### **Core Concepts**
- **Recurrence Relation:** Defines runtime as a function of smaller subproblems (here, t(n)=1+t(n/2)t(n) = 1 + t(n/2)t(n)=1+t(n/2)).
- **Divide by 2 Strategy:** Reduces problem size exponentially instead of linearly.
- **Logarithmic Growth:** Halving each time means the total number of calls grows with **log₂(n)**.
- **Efficiency Gain:** The improved method runs much faster than the linear version O(n)O(n)O(n).
##### **Simplified Notes**
- Recursive power calculation halves n each step instead of subtracting 1.
- Fewer calls → faster execution: only about **log₂(n)** recursive calls.
- **Time complexity:** O(log⁡n)O(\log n)O(logn).
- **Note simplified:** By halving the problem each call, the power method grows logarithmically, not linearly.

## Tail Recursion
- This section introduces **tail recursion**, which occurs when a recursive method’s **final action** is another recursive call.
- Example (tail-recursive `countDown`):
    
    ```java
    public static void countDown(int integer) {
        if (integer >= 1) {
            System.out.println(integer);
            countDown(integer - 1);
        }
    }
    ```
    
    → The last action (`countDown(integer - 1)`) is recursive, making this **tail recursion**.
- Tail recursion can be easily replaced with iteration because it just repeats the same logic with updated values.
- Converting to iteration:
    ```java
    public static void countDown(int integer) {
        while (integer >= 1) {
            System.out.println(integer);
            integer = integer - 1;
        }
    }
    ```
    → This removes the need for multiple activation records, saving memory.
- Some programming languages **automatically optimize** tail recursion by converting it to iteration behind the scenes (Java does not).
##### **Core Concepts**
- **Tail Recursion:** The recursive call is the method’s last operation.
- **Iteration Equivalent:** Tail recursion can always be rewritten as a loop.
- **Optimization:** Tail-recursive calls can be converted to loops to save **memory overhead** from recursion.
- **Java Limitation:** Java doesn’t perform automatic tail-recursion optimization, unlike some other languages.
##### **Simplified Notes**
- Tail recursion = recursion that ends with a recursive call.
- It repeats the same logic, so a loop can replace it easily.
- Saves memory if converted to iteration.
- **Note simplified:** Tail recursion acts like a loop and can be rewritten iteratively to reduce memory use.

## Using a Stack Instead of Recursion
- This section explains how **recursion can be replaced with iteration** by manually **simulating the program stack**.
- Example: The recursive method
    ```java
    public void displayArray(int first, int last) {
        if (first == last)
            System.out.println(array[first]);
        else {
            int mid = first + (last - first) / 2;
            displayArray(first, mid);
            displayArray(mid + 1, last);
        }
    }
    ```
    can be rewritten using a **stack** to mimic the recursive call process.
- Each recursive call in Java automatically pushes an **activation record** (which stores method parameters and local variables) onto the program stack.
- To simulate this behavior, we define a small **Record** class to hold the parameters `first` and `last`, and use a custom stack structure (`LinkedStack<Record>`).
- The iterative version repeatedly pops and pushes these records until the stack is empty, effectively replicating recursion manually.
##### **Core Concepts**
- **Simulating the Call Stack:**  
    You can replace recursive calls by storing method arguments in a stack and processing them iteratively.
- **Activation Record:**  
    Each record holds necessary data (`first`, `last`) for one “call” of the method.
- **Stack Order Matters:**  
    Pushing records in reverse order ensures the correct processing sequence (since stacks are LIFO).
- **When to Use:**  
    This approach is most helpful when recursion causes stack overflow or when an iterative version is not obvious.
##### **Simplified Notes**
- Recursion can be replaced by iteration using a **custom stack** that stores the call data.
- Each record on the stack acts like a paused recursive call.
- The process repeats until the stack is empty (the equivalent of finishing all recursive calls).
- **Note simplified:** You can imitate recursion with a loop and a stack, but it’s only worth doing when no simple iterative solution exists.