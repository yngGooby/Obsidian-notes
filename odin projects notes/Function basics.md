
### lesson overview

This section contains a general overview of topics that you will learn in this lesson.
- How to define and invoke different kinds of functions.
- How to use the return value.
- What function scope is.

## functions

- in JS parameters are items listed between parentheses, function arguments are what is decided to pass to the function
- by using the value the function(Ex: `function favoriteAnimal(value)`) we tell JS that we will send some value of our favoriteAnimal function, value is just a placeholder for some future value
- a good example is this 
	- ![[Pasted image 20260112000256.png]]
	- its also possible to pass in a function as am argument in a different function call
		- ![[Pasted image 20260112000407.png]]

## JS info function basics

- a variable declared inside a function is only visible inside that function
- a function can access an outer variable
	- you can also modify an outer variable inside a function
- When you modify an outer variable inside a function, the change does not affect the variable outside the function, so it keeps its original value.
	- modern code has few or no globals.
	- arbitrary data: data that can be any format, value, or structure not constrained by predefined rules
- a parameter: variable listed inside parentheses in the function declaration
- **argument**: value that is passed to the function when called

- bullish coalescing operator `??`
	- treats null and undefined similarly, it returns the first argument if its not `null/undefined` otherwise the second one
	- good example is 
	```javascript
  // if count is undefined or null, show "unknown"
  alert(count ?? "unknown");
```
when you make a function you should add comments

## MDN functions

- you want to run code when the user types into a text box you use `addEventListner()` expects you to pas it at least two parameters
	- name of the event to listen to 
	- function to run when the event happens
- instead of defining a seperate `logkey()` function you can pass an anonymous function into `addEventListner()`
- When a key is pressed, the browser automatically calls your function and passes in an event object, so the function’s event parameter receives that object and lets you access things like event.key.
	- ![[Pasted image 20260112192242.png]]
		- cant really understand how the second one works, but functions do not need a name so its just the function and the parameter
			- `event.key` just calls on the functions parameter and the `.key` logs what the user does and the console prints it
	- you cannot declare the same constant twice in the same scope
- function expression vs function declaration
	- `function declaration` declared as a seperate statement in the main code flow
		- can be called anywhere in their scope even before their definition
		- when inside a function in strict mode, only visible within that block
			- ![[Pasted image 20260112194439.png]]
	- `function expression` created inside an expression or inside another syntax construct, the function is created on the right side of the "assignment expression"
		- can only be use after its definition within the scope where it appears
			- ![[Pasted image 20260112194427.png]]
- anonymous function are functions that dont have a name but are expected to receive another function as a parameter
TO REMEMBER
	javascript is much more built-in and utility heavy, meaning you dont have to write so much code to achieve something simple
		- example
			- you would need to write a whole algorithm to get a basic last letter function but with JS its literally slice(-1)
