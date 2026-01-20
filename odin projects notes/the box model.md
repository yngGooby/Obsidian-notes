- Blocks and inline boxes

-  boxes have a inner display type and outer display type, you can set different values for display using "display" property.
    - ==if a box has a display value of block==
	    - the box go into a new line
	    - width and height are will be prioritized
	    - padding, margin, border cause other elements to be pushed away from box
	        if width isn't specified the box will extent into [[inline direction]] to fill the space in container, usually filling it to 100% of the space  
    
    - ==if box has a display type of inline==
	    - box will not go into a new line
	    - width and height properties are not meaningful/applied
	    - ==top - bottom padding, margins, borders apply== but not cause other inline boxes to move away from box
	    - left and right padding, margins, borders apply and ==cause other inline boxes to move away from box==
	    

- ### Inner and outer display types
- you can change inner display values, example =="display: flex;"== the element will still have an outer display type of "block" but will change the inner display type to flex. since we change the inner display type to flex, ==any direct children of the box will become flex items and behave with the flex property==
- a thing to remember, changing the value of the display property can change whether the outer display type of a box is block or inline which changes how things display alongside other elements in the layout.

- ### Parts of a box
- ==content box==: area where content is displayed, sizing it using properties width and height
- ==Padding box==: is what sits around content as white space, size it using padding
- ==Border box:== wraps the content and any padding, size it with "padding"
- ==Margin box:== the outermost layer, wrapping content, padding, border as whitespace between the box and other elements. Size it using margin
- ![[box-model-1.png]]

- ### The standard CSS box model
- if width and height are set on a standard box they are then transferred to content box. padding and borders are added to dimensions to get total size taken up by the box.


- ### Box sizing / alternative box model
	box sizing allows the inclusion of padding and border in an elements total width and height
		- to make a ==alternative box model==, set ==box-sizing: border-box== on it

### CSS tricks with margins
-  ==margin a shorthand property accepts up to four values==
		  - margin top
		  - margin right
		  - margin bottom
		  - margin left
	if one value is set then its automatically assumed the value for other values
##### Auto and centering
-  auto just makes the browser define a value for you, used for horizontal centering
	*if width isn't specified then auto effect has no effect*
#### collapsing margins
- vertical margins that touch each other will collapse (no padding content or borders separating)
#### negative margins
- will either pull element itself in that direction or pull element towards it