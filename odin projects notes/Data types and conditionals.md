### Lesson overview
This section contains a general overview of topics that you will learn in this lesson.
- Name the eight data types in JavaScript.
- Understand the difference between single, double, and backtick quotes.
- Embed a variable/expression in a string.
- Understand what a method is.
- Name the three logical operators.
- Understand what the comparison operators are.
- Understand what conditionals are.
- Understand what nesting is.
- Understand what truthy and falsy values are.

## strings
- you can wrap JS vars/expressions inside `${}`
	- `const greeting = 'Hello, ${name}';`
	- you can also do this to join together two variables
		- `const joined = '${one}${two}';`
		- joining the two strings is often referred to as concatenation
		- cant use those for normal strings only for adding outside variables 
- prompt function `prompt()` it ask the user to answer a question with a pop up and stores the text when its entered
- to break a string in parts use `\n`
- if you have a number value that you want to convert into a string use 
	- `Number()` converts anything passed to it into a number if it can
	- `String()` converts its argument to a string 

## w3 JS string methods
- to check length of a string use `length`
- there are 4 ways to get string characters
- `slice()` extracts part of a string and returns the extracted part in a new string
	- ![[Pasted image 20260106194048.png]]
	- returns: Banana
- `substring()` similar to `slice()` difference is start and end values less than 0 are treated as 0
- `toUpperCase, toLowerCase` makes a text either all caps or lowercase
- `isWellFormed()`, checks if a string is well formed if not returns false
- `toWellFormed()`, returns a new string where all lone surrogates are replaced with unicode
- `trim()` removes whitespace from both sides of a string
- `trimStart()` removes whitespace from the start of a string
- `padStart()` pads a string from the start `xxxYes`
	- `let text = 5, ; padded = text.padStart(4,'x');`
- `padEnd()` same thing but at the end 
- `repeat()`
	- The `repeat()` method returns a string with a number of copies of a string.
	- The `repeat()` method returns a new string.
	- The `repeat()` method does not change the original string.
- `replaceAll()` replaces a specified expression instead of a string 
	- `text = text.replaceAll("Cats","Dogs");`
		- replaces the word cats with dogs

## Conditionals 

- you can check to see if a string is greater than the other
- when comparing values of different types JS converts the values to numbers
- 1 and 0 are seen as t/f statements
	- `if(name == 1 || name == 0)`
```
const helloWorld = require('./helloWorld');
describe('Hello World', function() {
  test('says "Hello, World!"', function() {
    expect(helloWorld()).toEqual('Hello, World!');
  });
});
```

- `require()` import the code from the JS file `('helloWorld.js)` so it can be run
- `desecribe()` body of the test, it runs your code and testing to see if the output is correct
- `test()` function describes what should happen in English and includes `expect()`
```
const helloWorld = function() {
  return ''
} 
module.exports = helloWorld
```

- `module exports` how we export the function so that it can be imported with `require()` in the specific file
- to test JS files you must use `npm test <filename>.spec.js`
	- this is how you run it with node
- 

 