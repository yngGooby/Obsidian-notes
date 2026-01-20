### [Lesson overview](https://www.theodinproject.com/lessons/foundations-axes#lesson-overview)

This section contains a general overview of topics that you will learn in this lesson.

- You’ll learn about the 2 “axes” of a flex container.
- You’ll learn how to change those axes to arrange your content in columns instead of rows.

## Axes
- default direction for a flex container is horizontal or `row`, you can change it to vertical or `column`
	- use `flex-direction` for these properties
	- `row:` makes it left to right, `flex-basis` refers to `width`
	- `column:` goes top to bottom, `flex-basis` refers to the height
- `flex-direction: column` cannot work if you use `flex: 1` due to the `flex-basis` or `flex-grow/flex-shrink` starting their calculations at `0`
	- empty divs have 0 default height
- you fix this by using `flex: 1 1 auto` telling flex items to default their given `height` 
- you can also put a height on the parent `.flex-container` or use `flex-grow: 1`
- `flex-basis` refers to height
- 