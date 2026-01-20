
## A Simple Solution to a Difficult Problem
- This section introduces the **Towers of Hanoi** problem — a famous puzzle used to teach **recursion and algorithmic thinking**.
- The setup involves **three poles** and several **disks of different sizes**, stacked on the first pole from **largest (bottom)** to **smallest (top)**.
- The goal: **move all disks from pole 1 to pole 3** while following three strict rules:
    1. Only **one disk** can be moved at a time.
    2. You can **never place a larger disk on top of a smaller one**.
    3. The **second pole** can be used as a temporary storage pole.
- For **three disks**, a sequence of **seven moves** solves the puzzle (listed step-by-step in the passage)
- With **four disks**, the puzzle requires **15 moves** — and as the number of disks increases, the complexity grows rapidly.
- While finding a solution by **trial and error** becomes impractical with more disks, a **recursive algorithm** can systematically solve the problem for **any number of disks**.
##### **Core Concepts**
- **Recursive Problem Structure:**  
    The task of moving _n_ disks can be broken into smaller versions of the same problem (move _n−1_ disks).
- **Exponential Growth:**  
    The number of moves doubles with each additional disk (pattern: 1, 3, 7, 15, ...).
- **Algorithmic Challenge:**  
    Demonstrates how recursion simplifies problems that are otherwise tedious to solve manually.
##### **Simplified Notes**
- Three poles, several disks: move all from pole 1 → pole 3.
- Rules: one disk at a time, no larger disk on smaller, use pole 2 as storage.
- 3 disks → 7 moves; 4 disks → 15 moves.
- A **recursive algorithm** can easily find the solution pattern for any number of disks.
- **Note simplified:** The Towers of Hanoi shows how recursion solves problems that grow too complex for trial and error.

## Aside
- This section fully develops the **Towers of Hanoi problem**, explaining its recursive solution, efficiency, and variations.
- **Setup:** Three poles, multiple disks of different sizes stacked on pole 1 (largest at bottom, smallest on top).  
    **Goal:** Move all disks from pole 1 to pole 3 while following 3 rules —
    1. Only one disk can be moved at a time.
    2. Never place a larger disk on a smaller one.
    3. You can use the second pole for temporary storage.
- **Recursive breakdown:**
    - Move the top _n–1_ disks from start → temp pole.
    - Move the bottom (largest) disk from start → end pole.
    - Move the _n–1_ disks from temp → end pole.
- **Base case:** When only one disk remains, move it directly (no recursion needed).
- **Algorithm (simplified version):**
    ```
    solveTowers(n, start, temp, end)
    if (n > 0)
       solveTowers(n−1, start, end, temp)
       Move disk from start → end
       solveTowers(n−1, temp, start, end)
    ```
- **Efficiency:**
    - Recursive calls follow the pattern: **m(n) = 2m(n−1) + 1**
    - Solving gives **m(n) = 2ⁿ − 1** → exponential growth (**O(2ⁿ)**).
    - This means doubling disks more than doubles moves (e.g., 3 disks = 7 moves, 4 = 15, 5 = 31, etc.).
- **Proof by Induction:** Confirms that both the recurrence and formula are valid for all _n ≥ 1_.
- **Legend Reference:** 64 disks would require 2⁶⁴ − 1 ≈ 1.8×10¹⁹ moves — making the monk legend impossible to complete.
- **Optimality Proof:** No algorithm can solve it in fewer moves; the recursive one is mathematically optimal.
- **Iterative versions:**
    - An iterative algorithm saves space but not time — still requires 2ⁿ − 1 moves.
    - You can replace **tail recursion** (the second recursive call) with a **loop** and swap poles each iteration.
    - The hybrid algorithm combines iteration with recursion by looping until no disks remain
##### **Core Concepts**
- **Recursive Structure:** Divide problem into smaller identical subproblems (move n–1 disks).
- **Base Case:** Smallest solvable instance (1 disk).
- **Recurrence Relation:** m(n) = 2m(n−1) + 1 → exponential time O(2ⁿ).
- **Proof by Induction:** Validates correctness and optimality.
- **Tail Recursion Conversion:** Can replace the last recursive call with iteration to reduce memory use.
- **Exponential Growth:** Doubling disks ≈ doubling recursive depth and more than doubling moves.
##### **Simplified Notes**
- Recursive Towers of Hanoi: 3 steps → move smaller pile, move biggest disk, move smaller pile again.
- **Time complexity:** O(2ⁿ), meaning moves double each time a disk is added.
- **Optimal:** No faster algorithm exists — recursion already achieves the minimum moves.
- Iterative versions save memory but not time.
- **Note simplified:** Towers of Hanoi perfectly shows recursion’s power — elegant but exponentially slow.
## A Poor Solution to a Simple Problem
- This section shows how the **recursive Fibonacci algorithm**, though elegant, is **extremely inefficient** due to redundant calculations.
- **Fibonacci definition:**
    
    ```
    F0 = 1, F1 = 1
    Fn = Fn−1 + Fn−2  (for n ≥ 2)
    ```
    
- **Recursive version:**
    
    ```java
    Fibonacci(n)
    if (n <= 1)
        return 1
    else
        return Fibonacci(n−1) + Fibonacci(n−2)
    ```
    
- Each call makes **two recursive calls**, creating overlapping subproblems (e.g., Fibonacci(n−1) calls Fibonacci(n−2) again).
- Example for **F6**: many numbers (like F3, F2) are recomputed multiple times; the same work repeats exponentially.
- **Iterative version** only computes each term once, making it far more efficient.
##### **Time Efficiency**
- Recursive relation:
    ```
    t(n) = 1 + t(n−1) + t(n−2)
    t(1) = 1, t(0) = 1
    ```
    mirrors the Fibonacci sequence itself.
- It can be proven that **t(n) > Fn**, meaning the time required grows at least as fast as Fibonacci numbers.
- Using the closed-form expression:
    ```
    Fn ≈ ( (1 + √5)ⁿ / √5 )
    ```
    and since (1 + √5)/2 ≈ 1.6,  
    → **t(n) = Ω(1.6ⁿ)** → exponential time.
- Therefore, **recursive Fibonacci is O(2ⁿ)** — impractical for large n.
- **Iterative Fibonacci**, on the other hand, uses a simple loop that performs **n−1 additions (O(n))**.
##### **Programming Tip**
- Avoid recursive methods that **recalculate the same values** repeatedly — they waste both time and memory.
##### **Questions**
- **Q3:** Recursive computation of F6 makes **25 recursive calls** and performs **9 additions**.
- **Q4:** Iterative computation of F6 performs **5 additions** (one per term after F1).
##### **Simplified Notes**
- Recursive Fibonacci is neat but terribly slow because it repeats the same subproblems.
- Time grows exponentially → O(2ⁿ).
- Iterative version is much faster → O(n).
- **Rule:** Never use recursion that recomputes already-solved cases.

## Languages and Grammars
- A **language** is a set of character sequences that follow specific **grammar rules**.
- **Symbols used:**
    - `x | y` → x or y
    - `x y` → x followed by y
    - `<s>` → instance of symbol s defined elsewhere.
## The Language of Java Identifiers
- A **Java identifier** is made of **letters, digits, or `$`**, cannot start with a digit, and has **no spaces**.
- The **grammar** is recursive:
    ```
    identifier = letter | identifier letter | identifier digit
    letter = a|b|…|z|A|B|…|Z|$
    digit = 0|1|…|9
    ```
- Meaning: an identifier is a **letter**, or an existing identifier followed by a **letter or digit**.
- Recursive grammars like this allow easy **recognition algorithms**.
- Example pseudocode for `isIdentifier`:
    
    ```
    if length == 1 → true if it's a letter
    else if last char is letter/digit → check rest recursively
    else → false
    ```
- **Q5:**
    
    - `AB5` → true
        
    - `A?B` → false (contains invalid character).
- **Q6:** Grammar for palindromes:
    
    ```
    palindrome = letter | ε | letter palindrome letter
    ```
- **Q7:** Pseudocode:
    
    ```
    if length ≤ 1 → true
    else if first == last → check substring without them
    else → false
    ```
## The Language of Prefix Expressions

## Evaluating Prefix Expressions
- **Infix expressions** place operators between operands (like `a + b * c`) and rely on **precedence**, **associativity**, and **parentheses** to avoid ambiguity.
- **Prefix expressions** put operators **before** operands (`* + a b c`), while **postfix** puts them **after** (e.g., `a b + c *`).
- To convert a **fully parenthesized infix** to prefix: move each operator to the open parenthesis `(` position, then remove parentheses →  
    `((a+b)*c)` → `* + a b c`.
- To convert to **postfix**, move operators to the close parenthesis `)` position →  
    `((a+b)*c)` → `a b + c *`.
- **Prefix grammar:**
    ```
    prefix = operand | operator prefix prefix
    operand = a | b | ... | z
    operator = + | - | * | /
    ```
- A string is a **prefix expression** if it’s either a single operand or has the form `<operator><prefix><prefix>`.
- Example: `+*ab−cd` is valid because `+` applies to `*ab` and `−cd`, both valid prefixes.
- **Recognition pseudocode:**
    - `endPre(str, first)` finds the end index of a prefix expression starting at `first`.
    - `isPrefix(str)` checks if the whole string matches one prefix expression by verifying `endPre(str, 0)` equals the last index.
- **Q8:** Prefix of `(a/b)*c−(d+e)*f` → `− * / a b c * + d e f`
- **Q9:** Infix of `−−a /b+c *d e f` → `((a - (b / (c + (d * e)))) - f)`
- **Q10:** `+−/abc*def*gh` → **No**, it has extra unused symbols (not two complete prefix subexpressions).
- **Q11:** Postfix of `((a+b)*c)` → `a b + c *`
- **Q12 (Trace):** `endPre("+*ab−cd",0)`
    - Finds `*ab` as first prefix → returns index `3`
    - Finds `−cd` as second prefix → returns index `6`.
- *_isPrefix("+_ab−cd")__ → true (valid prefix expression).

## **Indirect Recursion**
- Some recursive algorithms make their calls **indirectly** through other method rather than directly calling themselves.
- Example: Method A → calls Method B → calls Method C → calls Method A again.
- This is known as **indirect recursion**, which is harder to trace but arises naturally in certain algorithms.
- A special case where only two methods call each other is called **mutual recursion**.
### **Example: Expression Grammar**
- A valid algebraic expression in restricted infix form follows these rules:
    1. An **expression** is either a term or two terms separated by `+` or `−`.
    2. A **term** is either a factor or two factors separated by `*` or `/`.
    3. A **factor** is either a variable or a parenthesized expression.
    4. A **variable** is a single letter.
- Four methods can test each structure:
    - `isExpression()` calls `isTerm()`
    - `isTerm()` calls `isFactor()`
    - `isFactor()` calls both `isVariable()` and `isExpression()`
    - `isVariable()` checks a single character.
- These interconnected calls illustrate **indirect recursion**.
## **Backtracking**
- **Backtracking** is a problem-solving strategy that retraces steps to find alternate solutions when the current path fails.
- It involves exploring one possibility at a time, and if a dead end is reached, it “backs up” to the last valid decision point and tries another route.
- This approach resembles **brute force**, but instead of testing all options blindly, it **systematically prunes** impossible or unnecessary cases.
- Though potentially time-inefficient, it’s often the only viable solution when no better method exists.
- If the search space is small or well-structured, backtracking can still be efficient.
- ## note 
- A **brute-force** algorithm tests _every possible case_ (e.g., sequential search through an array).
- **Backtracking** is more efficient since it avoids paths that clearly cannot lead to a solution.
    
- It’s still exhaustive, but it eliminates large portions of the search space.
## **Maze Solving Example**
- A maze can be represented as a grid of squares, with each square representing one possible position.
- You can use recursion and backtracking to find a path from the entrance to the exit.
- The algorithm checks if the current square is valid (inside, clear, and unvisited).
- If it’s the **exit**, the search succeeds.
- Otherwise, mark it as visited and recursively try moving in each direction (south, east, north, west).
- If all moves fail, backtrack to the previous square and try a different direction.
- Each successful move marks the square as part of the solution path; unsuccessful ones remain marked as visited but not part of the final path.
- This ensures every possible route is explored without revisiting already failed paths.
- Backtracking can be used to find **any** path or modified to find the **shortest** one by counting steps and pruning longer paths.
## **n-Queens Problem**
- The **n-queens problem** asks to place `n` queens on an `n×n` chessboard so that no two queens attack each other.
- A queen can attack along **rows, columns, and diagonals**, so each queen must be the only one in its row, column, and both diagonals.
- The challenge is to find valid placements satisfying these conditions.
### **Historical Context**
- Introduced in 1848 as the **eight-queens problem**, asking how to place eight queens on a standard chessboard.
- It was solved in 1850, with **92 distinct solutions** published later.
- There are over 4 billion possible arrangements, but restricting to one queen per row and column reduces it to `8!` (40,320) possible combinations.
### **Solving the Problem**
- Place one queen in each column.
- For each column, choose a row where the queen is **not under attack** from previously placed queens.
- If no safe square exists in a column, **backtrack** to the previous column and move that queen to its next available row.
- Continue this process recursively until:
    - All queens are placed successfully (solution found), or
    - You backtrack past the first column (no solution exists).
### **Algorithm Summary**
1. Start in the first column.
2. Place a queen in the first safe square.
3. Recursively attempt to place a queen in the next column.
4. If the next column has no valid position, backtrack and move the previous queen.
5. Continue until all columns are filled or all configurations fail.
6. Each successful placement chain corresponds to a valid solution.
### **Recursive Pseudocode Overview**
```
placeQueens(column):
    if (column > number of columns)
        problem solved
    else
        while (rows remain and solution not found):
            find next safe row
            if (row found):
                place queen
                if (!placeQueens(column + 1)):
                    move queen to next row
                else:
                    return true
        remove queen
        return false
```
## note
- The solution starts with `placeQueens(firstColumn)` and ends once all queens are safely placed.
- If successful, the board can be displayed showing the final arrangement.
- **Indirect recursion:** Recursive calls can go through other methods; sometimes simplified to mutual recursion.
- **Backtracking:** A recursive search that reverses when stuck; efficient for small or pruned search spaces.
- **Maze solving:** Marks, searches, and backtracks; a clear example of recursion with state marking.
- **Design Decision:** Use backtracking only when other efficient methods don’t exist.
- **n-Queens:** Classic example of recursion plus backtracking, with factorial-level complexity.
