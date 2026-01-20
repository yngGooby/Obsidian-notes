
### Lesson overview
This section contains a general overview of topics that you will learn in this lesson.
- You’ll learn the 3 properties that are defined by the `flex` shorthand, and how to use them individually.

## the flex shorthand
- flex declaration is shorthand for 3 properties that can set on a flex item
	- they affect how flex items size themselves within their containers
- `shorthand property:` are css properties that let you set the values of multiple other css properties simultaneously.
	- can help to write more concise (easily readable) stylesheets
```
div {
	flex: 1;
}
```
flex 1 equates to flex-grow: 1, flex-shrink: 1, flex-basis: 0.
## flex grow
- uses a single number for value
- when applying flex grow (`flex-grow: 1;`) to a container we're telling every div to grow the same amount.
	- results in every div ending up the exact same size
- if you add `flex-grow: 2` to a single div then that div would grow 2x the size of the others
- `flex: 1 1 0%` means grow = 1(grows equally with others) shrink 1(can shrink if needed) and basis = 0% (starts at zero width so space is split evenly)
## flex-shrink
- `flex shrink` ends up being applied if the size of all flex items is larger than their parent container.
	- ex: think about it as 3 book on a shelf where each book needs to be 100px wide, but if the shelf is only 205px wide, the books squeeze themselves thinner so all three can still fit on the shelf instead of one falling off
	- ex: if our 3 divs from above had a width declaration like: `width: 100px`and `.flex-container` was smaller than `300px`, our divs would have to shrink to fit.
- default shrink is `flex-shrink 1`
	- all items shrink evenly
- if you don't want an item to shrink then specify `flex-shrink: 0`
	- can also specify higher numbers to make certain items shrink at a higher rate than normal
- IMPORTANT
	- when specifying `flex-grow` or `flex-shrink`, flex items do not respect given values for width. 
		- if a parent is big enough then it'll grow to fill it
		- if a parent is too small, it'll shrink them to fit
			- it isn't a bug
## flex basis
- sets initial size of a flex item
- default value is `flex-basis: 0%`
	- if using auto as a flex-basis tells the item to check for a width declaration
	- difference between the default value of `flex-basis` and  `flex`
		- if no flex basis is given, actual default value for flex-basis is auto
		- when specified `flex:1` on element its interpreted as `flex:1 1 0`
		- if you want to only adjust an items `flex-grow` do so directly without shorthand
		- `flex: 1 1 auto` same as `flex: auto`
 
## what is flex auto
- is equivalent to the values of `flex-grow: 1, flex-shrink: 1, flex-basis: auto` or `flex: 1 1 auto`
## w3c's basic values of flex
- ## flex: initial 
	- same as `flex: 0 1 auto`, sizes the item based on width/height properties
	- makes the flex item inflexible when there is "positive" free space but allows shrinkage to minimum size when there's insufficient space.
	- alignment abilities/auto margin's can be used to align flex items along the main axis
- ## flex: auto
	- same as `flex: 1 1 auto` sizes the item based on width/height properties
	- makes them fully flexible
		- absorbs any free space along the main axis
	- if all items are either `flex: auto`, `flex: initial`, `flex: none` any positive free space after the items have been sized will be distributed evenly to the items with `flex: auto`
- ## flex: none
	- same as `flex: 0 0 auto` sizes the item based on width/height properties
	- makes flex item fully inflexible same as `initial` difference is flex items are not allowed to shrink even in overflow situations
- ## flex: `<number [1, infinity]>`
	- makes the flex item flexible and sets the flex basis to zero
		- results in an item that receives the specified proportion of the free space in the flex container
	- if all items in the flex container use this pattern, their sizes will be proportional to the specified flex factor

## you can target a child in a container with 
- EX: .container > .search![[Pasted image 20251216162616.png]]
