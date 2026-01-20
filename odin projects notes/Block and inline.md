### [Lesson overview](https://www.theodinproject.com/lessons/foundations-block-and-inline#lesson-overview)

This section contains a general overview of topics that you will learn in this lesson.

- You’ll learn about “Normal flow”.
- You’ll learn the difference between `block` and `inline` elements.
- You’ll learn which elements default to `block` and which elements default to `inline`.
- You’ll learn what divs and spans are.


### block vs inline
- block elements are stacked on each other, each element starts on new line
- inline start with any elements its placed beside.
#### divs
- boxes that can contain anything
- can be given id and classes for css styling
- div is block leveling element by default(container element) allows us to divide the page into different blocks

#### spans
- inline level element
- used to group text content, inline HTML elements for styling
- should be used when you want to style or affect a small piece of text inside a line without breaking the flow of the paragraph.
  
  ### mdn "normal flow"/intro to CSS layout
- [[margin collapsing]] - two vertically adjacent elements both have a margin set on them and margins touch, larger margin stays and smaller one disappears(only relevant in vertical direction)
- #### ways to override normal flow
	-  ==display property==; by using block, inline, inline-block
	-  ==floats==; such as left value, causes block-level elements to wrap along an element
	- ==positioning==; allows for precise control of box placement inside other boxes. Static is default normal flow

#### inline block
- allows to set width and height on an element
- `display: inline` top, bottom margins are not respected, only with display: `inline-block`
	- #### difference between `display: inline block` and `display: block`
		- **display block**: line break happens after element so it block element doesn't sit next to other elements 
			- `display: inline`: blocks will overlap text 
			- `display: inline-block:`blocks will not overlap text
			- `display: block: `Elements are stack on each other not next to 