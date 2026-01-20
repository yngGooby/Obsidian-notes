
After studying this chapter, you should be able to
- Describe the operations of the ADT stack
- Use a stack to decide whether the delimiters in an algebraic expression are paired correctly
- Use a stack to convert an infix expression to a postfix expression
- Use a stack to evaluate a postfix expression
- Use a stack to evaluate an infix expression
- Use a stack in a program
- Describe how the Java run-time environment uses a stack to track the execution of methods

### Stack

- When you add an item to a stack you place it on top of the stack, when  you remove an item you remove the item most recently added. So when removing an item you remove the item added most recently " that is, the last item added to the stack is the first one removed"

- ==`LAFO`==: Last-in first out 
- ==`ADT STACK`==: organizes its entries according to the order in which they were added.
				- additions are to one end of the stack called the "top"
				- top entry is the newest item among the items currently in the stack
	Stack example
	![[Pasted image 20250909212813.png]]
		- a client can look at or remove only the top entry
		- only way to look at an entry that isn't at the top is to repeatedly remove items from the stack until desired item reaches the top
		- if you remove all stack entries one by one, you'd get them in reverse chorological order,(most recent and ending with first item added to stack)
- ==`Push`==: operation that adds an entry to a stack
- ==`pop`==:  operation that removes an entry
- ==`peek`==: operation that retrieves top entry without removing it
- ==`isEmpty`==: detects whether the stack is empty
- ==`clear`==: removes all entries from the stack
- ##### what should pop and peek do when stack is empty?
			- they should not attempt to do so when a stack is empty but you must consider 3 possible actions by using the methods
				- assume that collection isn't empty; honor a precondition making that happen
				- Return `null`
				- throw an exception
					-first option makes sense for private methods since they are invoked only by other methods within the same class
					- pop and peek are public methods, they must handle the case of an empty stack instead of relying on the client to follow preconditions
					- if method signals failure by returning a value, must match the methods return type; using `null` only works if ADT doesn't allow `null` entries but stacks do, `null` would be ambiguous meaning it could either be an actual value or an empty stack forcing clients to call extra methods like `isEmpty` risking confusion and defeats its purpose.
				- so the decision is to make `pop` and `peek` throw an exception when stack is empty; for the design a return value of `null` will be considered invalid data
- #### Trust
	- ==`trusted code`==: when you can prove that code behaves correctly and securely
		- a private method in a class can reliably assume or trust that its precondition will be honored and its return value will be treated correctly
			- its considered calling `pop` or `peek` when a stack is empty to be a mistake by the client, thus throwing a runtime exception if application cant recover it can catch the exception and deal with it
### note: alternate names for methods
- ==`pull`== can sometimes be used as ==`pop`==
- ==`getTop`== can mean ==`peak`==
### security note: design guidelines
- use preconditions and postconditions to document assumptions
- do not trust that a client will use public methods correctly
- avoid ambiguous return values
- prefer throwing exceptions instead of returning values to signal a problem
# example problem
- ![[Pasted image 20250910000231.png]]
- ANSWER:  bottom: Jim, top: Sophia
- Question 2 Consider the stack that was created in Question 1, and define a new empty stack
	nameStack.
	1. Write a loop that pops the strings from stringStack and pushes them onto nameStack.
	2. Describe the contents of the stacks stringStack and nameStack when the loop that you just wrote
	completes its execution

## Using a Stack to Process Algebraic Expressions

==`binary operators`==: operators that have two operands
			- example; "The + in a + b is a binary operator"
==`unary operator`==: operators that only have one operand
			- example; "the minus sign in -5 is a unary operator"
- when an algebraic expression has no parentheses operations occur in PEMDAS
		- example; "evaluates as 20−2*2^2then as 20−16 and finally as 4."
- What happens when two or more adjacent operators have the same precedence?
		- exponentiations such a^b^c occur from right to left thus 2 ^ 2^ 3 means 2(2^3) or 28
		- other operations occur from left to right such as multiplication and division in an a*b/c or addition and the subtraction in a a - b + c therefore, 8 - 4 + 2 means (8-4)+2 or 6
		- parentheses in an expression override the normal operator precedence
	
- ==`infix expression`==; ordinary algebraic expression in which each binary operator appears between two operands
- ==`prefix expression`==: every binary operator infront of  its two operands 
- ==`postfix expression`==: every binary operator is behind its two operands
- ==`Polish notation`==: is what notation in a prefix is sometimes called
- ==Balanced equations==: contain delimiters that are correctly or are balanced
	- you would want an algorithm that detects whether an infix expression is balanced
	- example: `a€{b[c(d+e)/2−f]+1}` is balanced due to delimiters being used correctly
	- ![[Pasted image 20250910203218.png]]
- ==Unbalanced equations==: opening and closing symbols dont math up in order count or type
		- ![[Pasted image 20250910203207.png]]

		- to read this
			- left column shows what symbol is read
			- middle column shows how postfix builds up
			- right column shows the state of the operator stack after that step
## Infix-to-postfix conversion

- ![[Pasted image 20250910233329.png]]
 - ![[Pasted image 20250910232737.png]]
 - ![[Pasted image 20250910233703.png]]

- ==Postfix==: operator pops last two operands from stack
- ==Infix==: just normal math you use operator precedence and parentheses to decide order

- to convert an infix expression to postfix form 
	- ==operand==: append each operand to the end of the output expression
	- ==operator==: push ^ onto the stack
	- ==operator + - * or / ==: pop operators from the stack, appending them to the output expression until either the stack is empty or its top entry has a lower precedence than new encountered operator, push the new operator onto stack
	- ==open parenthesis==: push ( onto stack
	- ==close parenthesis==: pop operators from the stack and append them to the output expression until open parenthesis parenthesis is popped, discards both parentheses

### The Program Stack

- ==Program counter==: when a program executes a special location that references the current instruction
- ==Java Virtual Machine (JVM)==: to maintain computer independence, java runs the code on a vm
- ==Activation record/frame==: when a method is called the programs runtime environment creates this type of object.
	- ==Activation record==: shows the methods state during its execution contains methods arguments local variables and references to current instructions.
- ==Program stack/java stack==: activation record pushed onto a this stack, since one method can call another the program stack often contains more than one activation record, record at top of stack belongs to the method that is currently executing



### Missed things from chapter
- ==Explicit ADT definition/Stack ADT contract==: a collection of entries organized according to the order in which they were added (LIFO).
- ==Post Evaluation==: algorithm for evaluating a postfix expression with a stack
- ==Recursion tie-in==: each recursive call pushed a new activation record on the program stack; base case stops the growth