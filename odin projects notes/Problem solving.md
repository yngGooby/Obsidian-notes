
## lesson overview

- Explain the three steps in the problem solving process.
- Explain what pseudocode is and be able to use it to solve problems.
- Be able to break a problem down into subproblems.

## understanding the problem

- to really understand a problem, write it own on paper, reword it in plain English until it makes sense to you, and draw diagrams, when you can explain the problem to someone else you understand it

## plan

questions that you should be able to answer when planning is
- Does your program have a user interface? What will it look like? What functionality will the interface have? Sketch this out on paper.
- What inputs will your program have? Will the user enter data or will you get input from somewhere else?
- What’s the desired output?
- Given your inputs, what are the steps necessary to return the desired output?
	- the last question is when you write out an algorithm to solve the problem

## pseudocode

its writing out the logic for your program in a natural language instead of code

``` javascript
When the user inputs a number
Initialize a counter variable and set its value to zero
While counter is smaller than user inputted number increment the counter by one
Print the value of the counter variable

```
this is a good example of it

## divide and conquer

- when starting there's gonna be a lot of problems, pick the smallest or simplest one and start there with coding
	- usually when working one one subproblem you can identify the next one to work on
	- dont work on big problems in one go, you'll burn out

## solving fizz buzz

- Write a program that allows the user to enter a number, print each number between one and the number the user entered, but for numbers that divide by 3 without a remainder print `Fizz` instead. For numbers that divide by 5 without a remainder print `Buzz` and finally for numbers that divide by both 3 and 5 without a remainder print `FizzBuzz`.
- the `parseInt` function is used in the code so that a number is returned from a user input

## freecodecamp how to think like a programmer

- the best way to solve problems is by having a framework and practicing it
	- "Problem-solving skills are almost unanimously the most important qualification that employers look for….more than programming languages proficiency, debugging, and system design."
- **understand**
	- know whats being asked
	- you only understand a problem once you can explain it in plain english
	- write down the problem, doodle a diagram, or tell someone else about it
- **plan**
	- try and write down the exact steps
	- analyze the problem and process the info
	- USE COMMENTS
- **divide**
	- break down a big problem into sub problems and solve them individually 
	- then after solving as many subproblems "connect the dots"
- **stuck**
	- to get unstuck debug
		- go step by step through the solution you're trying to find where you went wrong
	- reassess, look at the problem from a different perspective, anything that can be abstracted to a more general approach
		- you can also delete everything and start with fresh eyes
	- dont look for solutions to the big problem, look for solutions to sub problems, unless you struggle you wont learn a thing
- **practice**
	- solve as many problems as you can
		- stuff like chess puzzles, math problems, sudoku etc.
		- most successful people have "micro problem solving"
		- find things that have problems and solve them to better help your critical thinking skills
## how to think like a programmer (hour video)

- **Bad beginner advice**
	- just start with a game
	- start with c++
	- if you use visual basic you don't have to code until the end
	- best way to start is to pick a problem you want to solve
	- you'll stay motivated if you work on a real world problem
- **Things that I wish I'd been taught**
	- programming isn't about the language
	- the language doesn't matter that much
	- there's not a lot of memorizing
	- most programming isn't about math
	- programming languages are simpler than human ones
	- programming is really about solving problems
	- its about explaining things to the "idiot" computer
- **code isn't about language**
	- coding has only about 8 main concepts
	- they work in almost the same way in every language
	- learn how to use these concepts in English
	- write out the concepts first, then convert to code later
		- if your lost in coding, then you shouldn't
	- most beginners think they don't understand what code to write
		- real problem is they don't understand the problem they're trying to solve
		- code yet
- **comments are code**
	- comments explain code to other programmers
	- code explains the comments to the computer
- **new variables**
	- name: what do we call this thing?
	- type: what type of data does this contain?
	- initVal: what is its starting value?
- **new variable algorithm**
	- you must write in English first
	- create whatever it is but the sentence must answer those questions
		- whats its name?
		- whats its starting value?
		- whats its type?
- **debugging**
	- issues when debugging that isn't correct
		- did you tell the computer what to do incorrectly
		- did you tell it to do the wrong thing
	- how to debug
		- best way to debug is to not have bugs
		- bad implementation can be googled
			- if you cant find the answer on google, might have bad algorithms or bad understanding of concepts
		- what parts are you not understanding
- **for loops**
	- how's it start
	- how's it finish
	- how it changes
- **while loop**
	- only 1 parameter implies a lot that it doesn't require

## builtin pseudocode 

- **main constructs of pseudocode**
	- pseudocode is the ability to represent six programming constructs
		- **sequence:** represents linear task sequentially preformed one after the other
		- **while:** loop with a condition at its beginning
		- **repeat-until:** loop with a conditional at the bottom
		- **for:** another way of looping
		- **if-then-else:** conditional statement changing the flow of the algorithm
		- **case:** generalization form of **if-then-else**
			- ![[Pasted image 20260114000849.png]]
	- those constructs are most often used to implement any algorithm
	- two most needed commands are
		- invoking classes or calling functions
		- handling exceptions
			- ![[Pasted image 20260114000953.png]]
	- **how to write pseudocode**
		- always capitalize the initial word
		- make only one statement per line
		- indent to show hierarchy, improve readability and show nested constructs
		- always end multi-line sections using any of the END keywords (ENDIF, ENDWHILE, etc.)
		- keep your statements programming language independent
		- use the naming domain of the problem, not that of the implementation
			- "Append the last name to the first name" instead of "name = first + last"
		- keep it simple, concise, and readable
- pseudocode make a complex big project can make the code part much easier
	- when writing out it helps realize possible problems or design flaws in the algorithm which can save time and effort on fixing bugs
- **why use pseudocode?**
	- its easier to read
		- often programmers work with other people outside the field and it makes communicating between different specialties easier and efficient
	- simplifies code construction
		- when programming you process, develope, and generate pseudocode, converting that into real code written in any language
	- good middle point between flowchart and code
		- moving from the idea to a flowchart, pseudocode makes the transition somewhat simpler
	- helpful starting point for documentation
		- can represent good starting point for what documentation should include
	- allows for quick bug detection
		- 