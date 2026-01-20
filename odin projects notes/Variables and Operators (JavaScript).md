
## Lesson overview
This section contains a general overview of topics that you will learn in this lesson.
- Running JavaScript code using an HTML file.
- Declaring variables with `let` and `const`.
- Performing number operations.
- Performing string operations.
- Using logical and mathematical operators.

## how to run JavaScript code
- `console.log()` is the command to print something to the developer console in the browser
- to include JS in a webpage is through external script
	- to do that link it by `<script src="javascript.js"></script>`
	- JS files have the extension `.js` similar to `.css` for stylesheets
## variables
- variables are the building block of a program
	- are to be thought of as storage containers for data in your code
- declare variables using `let`
- you can also reassign variables 
	- ```
	  let age = 11;
	  console.log(age);
	  
	  age = 54;
	  console.log(age);
	  ```
- use `const` if you dont want a variable to be reassigned

## numbers
- JS follows PEMDAS
	- parentheses first
	- exponents second
	- multiply third
	- divide fourth
	- add fifth
	- subtract sixth

## javascript.info variables

- `alert` creates a box to alert the user of something
- you can declare multiple variables in one like ex:
	- `let user = "john", age = 55, message = "Hello"`
	- but for readability sake don't do it!
- a good analogy for a variable is if its a box for data with a sticker on it for its name
	- message = hello
- you can also declare two variables and copy data from each other
	- `let hello = "hello world`
	- `let message;`
	- `message = hello`
- don't use the same variable name twice
- dollar sign $ and underscore _ can be used in names
	- use uppercase for aliases for hard to remember values and values that are hard-coded into the language
## javascript.info operators

- remainder `%`
	- the result of `a % b` is the remainder of the integer division of a by b
- exponentiation `**`
	- the result of `a ** b` raises `a` to the power of `b`
- you can add strings with binary
	- a good example is `alert('1' + 2)` would equal 12
	- another would be `alert(2+2+'1')` would be 41
- with pre and post fix adding to a variable
	- use postfix if you'd like to increase a value but use its previous value
	- use prefix if you and a value update immediately
	- if there isn't a increase/decrease then its not used, no difference in which form to use
- with division, subtraction, and multiplication it turns the string into a number
- to convert a string into a number use `+a` the plus to do that