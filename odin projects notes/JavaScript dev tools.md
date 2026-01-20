## lesson overview

This section contains a general overview of topics that you will learn in this lesson.
- Change screen size of a website with developer tools.
- View and change the DOM.
- Debug JavaScript.
- Use breakpoints.
- View and edit HTML in the Elements tab.
- View the Resources Panel to check the scripts running on a website.
- Add CSS Pseudostate to a Class.
- View CSS Properties in Alphabetical Order.
- View and edit the Box Model of any Element in Chrome Devotes.
- View a page in print mode.
- Enable or Disable CSS Classes.
- Simulate media queries in Device Mode.

## chrome dev tools - view and change CSS

- to add a class to a css property click on the element, inspect and with filter-styles search with .cls and make the new class name and add it to the element
- you can measure the width/height of an element when you hover over it in the elements panel
- html represents initial page content, DOM represents current page content
	- node in a DOM tree is just an element from HTML

## JS debugging in DOM

- Event listener break points pauses the code right before code executes
	- expand event listener break point section
		- expand mouse category
		- check click check box
	- you can set a break point on a line of code
		- when a DOM point changes
		- when exception is thrown
- you can debug a line of JS code with step through function, next line function and previous function
- you can add break points on line by selecting line code number
	- use resume skip execution and it'll run the code up until that line executes
	- use `typeof sum` to help debug and it'll identify why a certain value is appearing as is
- you edit a css file on `inspect` if you want experimental changes and only edit the real css file when you want perminate changes
	- Use **Inspect** to tweak until it looks right (instant feedback, no refresh).
	- Copy the working CSS.
	- Paste it into your CSS file.
	- Refresh once to confirm it still works.