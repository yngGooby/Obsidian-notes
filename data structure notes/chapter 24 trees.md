
## tree concepts/hierarchical organization
- Linear structures (stacks, queues, lists, dictionaries) store data in a straight line, but many real situations require grouping data into levels.
- Hierarchical (nonlinear) organization arranges data into parent–child relationships, forming a tree structure.
- Family trees are a basic example of hierarchical data, showing relatives across multiple generations and branches.
- Organizational charts (like universities, companies, governments) use hierarchy where roles report upward to higher positions.
- Computer file directories are hierarchical, with folders containing subfolders and files inside other folders.

**Simplified Summary**  
This passage explains that some data can’t be organized in a straight line, so we use hierarchical structures called trees. Family relationships, university staff charts, and computer file systems all show how things can be arranged in levels where some items contain or oversee others. These examples help visualize how tree structures group information into parent–child layers instead of one long list.

## Tree Terminology
- A tree is a set of **nodes connected by edges**, organized in **levels**.
- The **root** is the top node; it has no parent.
- Nodes with children are **parents**; nodes without children are **leaves**.
- A node’s children are **siblings** of each other.
- **Ancestors** are nodes above; **descendants** are nodes below.
- Any node and its descendants form a **subtree**.
### Types of Trees
- **General tree:** nodes can have any number of children.
- **n-ary tree:** each node has at most _n_ children.
- **Binary tree:** each node has **at most two children**, called **left** and **right**.
- Every subtree of a binary tree is also a binary tree
### Full, Complete, and Balanced Trees

- **Full binary tree:** all parents have exactly 2 children; all leaves are on the same level.
- **Complete binary tree:** all levels except the last are full; last level is filled left-to-right.
- **Completely balanced binary tree:** both subtrees of every node have equal height (only full trees qualify).
- **Height-balanced (balanced) trees:** subtrees differ by at most height 1.
### Height of a Tree
- Height = **number of levels**.
- A one-node tree has height **1**; an empty tree has height **0**.
- Height formula:  
    **height(T) = 1 + height of tallest subtree**
- Height is also **1 + longest path length from root to a leaf**.
### Height & Node Count (Full/Complete Trees)
- Full binary tree with height **h** has:  
    ∑i=0h−12i=2h−1\sum_{i=0}^{h-1} 2^i = 2^h - 1∑i=0h−1​2i=2h−1 nodes
- If a full/complete tree has **n** nodes:
    - n=2h−1n = 2^h - 1n=2h−1
    - h=log⁡2(n+1)h = \log_2(n + 1)h=log2​(n+1) (rounded up for complete trees)
## Simplified Summary
This section explains how trees work: they’re made of nodes arranged in levels with a root at the top, parents above, and children below. Leaves have no children, and any node with its descendants forms a subtree. Tree structures come in different forms—general, n-ary, and binary—depending on how many children each node can have. Binary trees can be full (every parent has two children), complete (filled left to right), or balanced (subtrees differ in height by at most one). A tree’s height counts how many levels it has, and full or complete trees follow a predictable formula where height is related to the number of nodes using powers of two.

## Traversals of a Tree / Traversals of a Binary Tree

##### General Traversal Ideas
- Traversing a tree means visiting each node’s data exactly once, and unlike lists, there is no single obvious order.
- “Visiting” a node means processing its data; a traversal might move past a node without visiting it yet.
- Binary tree traversals use recursion because each subtree is itself a smaller binary tree.
##### Preorder Traversal
- Order: Root → Left Subtree → Right Subtree.
- The root is processed before its children.
- This is a depth-first traversal.
##### Inorder Traversal
- Order: Left Subtree → Root → Right Subtree.
- Always processes the entire left subtree before the root.
- Produces sorted order in a binary search tree.
##### Postorder Traversal
- Order: Left Subtree → Right Subtree → Root.
- Children are processed before their parent.
- Useful for deleting or freeing structures from bottom to top.
##### Level-Order Traversal
- Visits each level from left to right before moving to the next level.
- This is a breadth-first traversal.
##### Depth-First vs. Breadth-First
- Preorder, inorder, postorder = depth-first.
- Level-order = breadth-first.
#### Simplified Summary
Tree traversals are different ways to visit every node once, and each one chooses a different moment to handle the root compared to its left and right subtrees. Preorder processes the root first, inorder does it in the middle, and postorder does it last. Level-order visits each level from left to right before going down. These patterns let you pick the order that best fits your task.

## Traversals in a General Tree/Java Interfaces for Trees

- General trees support **level-order**, **preorder**, and **postorder** traversals.
- **Inorder traversal is not defined** for general trees because nodes can have more than two children.
- Level-order visits nodes by levels starting from the root, just like in binary trees but allowing many children.
- Preorder visits the **root first**, then each subtree in order.
- Postorder visits **all subtrees first**, then the root last
- Trees vary widely, so a single universal tree interface would be too large and inflexible.
- Instead, Java uses **multiple smaller interfaces** that can be combined depending on the application.
- These interfaces and their implementing classes are grouped in a **package**, hiding internal details like node classes from the client.
#### Simplified Summary
General trees use level-order, preorder, and postorder traversals, but not inorder because they can have more than two children. Level-order visits one level at a time, preorder visits the root before its subtrees, and postorder visits the subtrees before the root. In Java, trees use several small interfaces rather than one big one, and these are organized into a package that hides internal implementation details.

##### TreeInterface (Fundamental Operations
- `TreeInterface<T>` defines the **basic operations all trees share**.
- Methods included:
    - `getRootData()` – returns the root’s data
    - `getHeight()` – returns tree height
    - `getNumberOfNodes()` – returns total nodes
    - `isEmpty()` – checks if tree is empty
    - `clear()` – removes all nodes
- It intentionally **does not include add/remove or traversal methods** because those depend on the tree type
##### TreeIteratorInterface (Traversal Methods)
- Traversals are handled separately through an iterator-based interface.
- Each method returns an iterator for a specific traversal:
    - `getPreorderIterator()`
    - `getPostorderIterator()`
    - `getInorderIterator()`
    - `getLevelOrderIterator()`
- A tree class can implement any or all traversal methods depending on what the application needs
##### BinaryTreeInterface (Specialized for Binary Trees)
- Binary trees are common, so they get a **specialized interface**.
- It extends both `TreeInterface` and `TreeIteratorInterface`.
- Adds two key methods:
    - `setRootData(T data)` – changes the root’s data
    - `setTree(rootData, leftTree, rightTree)` – forms a new tree from a root + two subtrees
- `setTree` builds a new binary tree using existing subtree objects.
- Interfaces cannot enforce constructors, so `setTree` acts as a constructor-like operation.
##### Example (Building a Binary Tree in Java)
- Each leaf (`D`, `F`, `G`, `H`) is created as a one-node tree.
- Subtrees are built bottom-up using `setTree`.
- The full tree is formed at the end (`A` as root).
- Example code prints:
    - Root data
    - Tree height
    - Number of nodes
    - Preorder traversal results
#### Simplified Summary
Tree interfaces are split into smaller parts so each tree type only includes what it needs. The basic `TreeInterface` includes universal features like getting the root, height, or node count. Traversals are handled in a separate interface that returns iterators for preorder, postorder, inorder, and level-order traversal. Binary trees get their own interface that extends both of these and adds methods to build a tree from a root and two subtrees. The example Java code shows how to build a binary tree

##### Expression Trees
- A binary tree can represent algebraic expressions where each **operator is the root of a subtree** and its two **children are operands**.
- Parentheses don’t appear in the tree because the structure itself defines the order of operations.
- Infix form: operator between operands (normal notation).
- Prefix form: operator before operands (produced by **preorder traversal**).
- Postfix form: operator after operands (produced by **postorder traversal**).
- Inorder traversal lists the expression in infix form but without parentheses.
##### Expression Evaluation
- A postorder traversal naturally evaluates an expression tree:
    - Evaluate left subtree
    - Evaluate right subtree
    - Apply the operator at the root
- The algorithm recursively combines subtree values to compute the entire expression.
##### Decision Trees
- A decision tree models choices: each **nonleaf node is a question**, and each **child is an answer path**.
- Leaves represent conclusions.
- Decision trees may be general trees but are often binary (yes/no).
- Users move through the tree by answering questions from root to leaf.
##### DecisionTreeInterface
- Extends `BinaryTreeInterface` and adds operations to:
    - Access and modify the **current node’s data**
    - Add responses (left = no, right = yes)
    - Move to left or right child
    - Check whether the current node is a leaf (an answer)
    - Reset to the root
##### Guessing Game Example
- The program asks yes/no questions stored in the tree to guess what the user is thinking of.
- If the program guesses wrong, the user supplies a new question and answer, and the tree is **augmented**.
- The incorrect leaf becomes a **new question node**, and two children are added:
    - One with the old guess
    - One with the new correct answer
- The system “learns” and becomes more accurate over time.
#### Simplified Summary
Expression trees use binary trees to represent algebraic expressions, where operators are internal nodes and operands are children. Traversals generate prefix, postfix, and infix versions of the expression, and postorder can evaluate the whole expression by computing subtrees first. Decision trees work differently: they store questions at each node and move through the tree as users answer yes or no, eventually reaching a leaf that represents a conclusion. In a guessing game, the tree grows whenever the program guesses incorrectly by adding new questions and answers, letting the system learn from each play.

##### Binary Search Trees (BSTs)
- A BST is a binary tree where each node’s data is **greater than all values in its left subtree** and **less than all values in its right subtree**.
- Every node is the root of its own BST.
- BSTs normally assume **distinct entries** to avoid complications.
- Multiple BST shapes can be formed from the same data—structure is **not unique**.
- Searching follows the BST rule:
    - If the value is smaller → search left
    - If larger → search right
    - If equal → found
- A search ends when a match is found or you reach an empty subtree.
- Search efficiency is **O(h)** where _h_ is tree height.
- A tall, skewed BST can be as slow as **O(n)** like a linked list search.
- Shorter (balanced) BSTs give faster searches.
    

##### Heaps
- A heap is a **complete binary tree** with a specific ordering rule.
- In a **maxheap**, every node is ≥ its descendants; root holds the **largest** item.
- In a **minheap**, every node is ≤ its descendants; root holds the **smallest** item.
- Subtrees of any node in a heap are also heaps.
- Unlike BSTs, heaps do **not** order left vs. right children relative to each other.
- Maxheap operations include: add, removeMax, getMax, isEmpty, getSize, clear.
- Removing repeatedly from a maxheap returns items in **descending order**.
- Heaps are commonly used to implement **priority queues**.

##### Priority Queues (via Heaps)
- A priority queue retrieves items by highest priority, not arrival order.
- Implemented efficiently using a maxheap.
- The adapter class uses a heap internally and exposes priority-queue operations.
#### Simplified Summary

A binary search tree organizes data so left children are smaller and right children are larger, which makes searching faster—but only if the tree stays short. A tall BST becomes slow like a linked list, while a balanced one gives quick searches. Heaps are different: they are complete binary trees where each node is larger (in a maxheap) or smaller (in a minheap) than everything below it, so the root always holds the highest-priority value. This property makes heaps perfect for priority queues, which always remove the largest or most important item first.

##### Parse Trees
- Parse trees are **general trees** used to test whether a string follows a given grammar.
- The grammar defines how valid algebraic expressions can be built using expressions, terms, factors, and variables.
- To check validity, we try to **derive the string from the grammar’s start symbol**, `<expression>`.
- If a full derivation is possible, it can be represented as a parse tree:
    - Root = `<expression>`
    - Internal nodes = grammar rules applied
    - Leaves = final symbols (variables, operators, parentheses)
- Parse trees are used by **compilers** to check syntax and generate executable code
##### Game Trees
- A game tree is a **general decision tree** representing all possible moves in a two-player game.
- Each node represents a **game state after a move**.
- Each child represents a possible **response move** by the opponent.
- These trees can be built ahead of time or generated as the program plays.
- Game trees help the program detect and eliminate bad strategies, improving gameplay over time.
#### Simplified Summary
Parse trees show how a string can be built from a grammar by breaking the expression down step by step until only variables and operators remain; compilers use them to validate code syntax. Game trees model all possible moves in a competitive game such as tic-tac-toe, where each node represents the board after one move and the children show all the opponent’s possible responses. These trees help programs evaluate strategies and improve gameplay.