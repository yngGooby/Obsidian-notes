
## lesson overview

- Name at least three kinds of JavaScript errors.
- Identify two parts of an error message that help you find where the error originates.
- Be able to understand how to research and resolve errors.

## the anatomy of an error
- `refferenceError` is thrown when one refers to a variable that isn't declared and or initialized within the current scope
- **stack trace** helps understand when the error was thrown in your application
- ![[Pasted image 20260116234754.png]]
	- this stack trace tells us
		- c isnt defined in the scope of `add()` which is declared on line 5
		- `add()` was called by `print()` which was declared on 9
		- `print()` itself was called on line 12
	- stack lets you trace the build up of the error back to its origin which was the declaration of `add()`

## common types of errors

- Syntax error
	- happens when code that needs to run isn't written correctly
- Reference error
	- a variable that doesn't reference or exist inside a scope
- type error
	- a operand or argument passed to a function is incompatible with the type expected by that operator or function
	- when attempting to modify a value that cant be changed
	- when attempting to use a variable in an inappropriate way
- when facing a `TypeError` its considered the data type you are trying to run a method or operation against, might not be what you think or the operation/method isnt compatible with that type

## tips for resolving errors

- error messages are good they lead you directly to the area of failure
- google the error, chances are you'll find a fix or explanation on Stackoverflow or in the documentation, you'll receive more clarity as to why you are receiving this error
- use the debugger in the developer mode in chrome
- make use of the `console.log()`, great for immediate feedback without needing to step through functions
	- other useful commands exist such as `console.table()` `console.trace()`

## errors vs warnings

- errors stop execution of your program
- warnings message's that provide insight on potential problems that may not crash your program at runtime or at all

## mdn What went wrong? Troubleshooting js

- `logic errors:` when syntax is correct but code is not what was intended to be, programs run well but give incorrect results
- 
