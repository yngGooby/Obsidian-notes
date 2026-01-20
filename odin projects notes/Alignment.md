### [Lesson overview](https://www.theodinproject.com/lessons/foundations-alignment#lesson-overview)

This section contains a general overview of topics that you will learn in this lesson.
- You’ll learn how to align items inside a flex container both vertically and horizontally.


## alignment
- `justify-content` aligns items across the main axis
	- `center`: centers items
	- `space-between:` gives gaps between items
- to change placement of items along the cross axis, use `align-items`
- `justify-content` and `align-items` are based on the main and cross axis of a container
	- their behavior can change when changing the `flex-direction` of a flex-container
- `justify-content` aligns items horizontally
- `align-items` aligns them vertically

## gap

- `gap` adds a specified space between flex items 
	- similar to adding a margin to items 
	- works reliably in modern browsers 

## joshwcomeau interactive guide to flexbox

- children will be positioned by default according to the following rules
	- `primary axis:` children will be bunched up at the start of the container
	- `cross axis:` children will stretch out to fill the entire container
- ## justify-content
	- `flex-start:` starts at either the left side (if row) or top (if column)
	- `center:` centers itself in the middle of the container
	- `flex-end:` ends at either the right side(if row) or bottom(if column)
	- `space-between:` evenly spaces the children but leaves no gaps if its from side to side or top to bottom
	- `space-around:` same as `space-between` but has space on the sides/top bottom
	- `space-evenly:` makes sure all children get the same/equal amount of space
- ## align-items/align-self
	- `stretch:` stretches the child from one end to the other, otherwise content is enclosed in its own space
	- `flex-start:` moves items to the start of the container (left side)
	- `center:` moves items to the center of the container
	- `flex-end` moves items to the end of the container(right side)
	- `baseline:` same as the flex-start
- align self has all these properties but its applied to the child element not the container
- fundamental difference between primary and cross axis 
	- **cross axis:** each flex items has its own line so items can move without colliding
	- **primary axis:** each item share a line so moving one item along this axis moves the others
- `justify:` position something along the primary axis
- `align:` position something along the cross axis
- `content:`a group of stuff that can be distributed
- `items:` single items that can be positioned individually
- when using thing like svg or pngs sometimes you don't want to use shrink as it can distort the image
- so items don't overflow out of a container you can use min-width and have it use 
	  `min-width: 0px` so it doesn't overflow
	  but it can break some things and make them worse so use it appropriately 