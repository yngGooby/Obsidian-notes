
#### Encapsulation
- ==`Encapsulation`==: a design principle of object oriented programming, it hides and encloses data and methods within a class
	- a good way to explain this is in a car things like pedals and steering wheels are visible but everything else in under the hood
- ==Abstraction==: process that ask you to focus on what instead of how
- "*That is, you should not worry about how the class’s methods will accomplish their goals. This separation of specification from implementation allows you to concentrate on fewer details, thereby making your task easier and less error-prone*"
- ==Interface==: describes everything needed to know about how to use a class, headers of public methods public names of constants 
- ==Implementation==: things live private data fields, private constants, all method definitions
		- ![[Pasted image 20250913231237.png]]
	- interface method names often end in "able" like Measurable but also endings such as "er" or interface are also used 
- you can use a java interface as you would use a data type when declairing a variable. 
		- Ex: method of `giveLastNameTo` can get a parameter type of `nameInterface`
		- `public voud giveLastNameTo (nameInterface aName);`
		- "*Why didn’t we declare aName’s type to be a class type such as Name? We want the interface to be independent of any class that implements it, since more than one class can implement an interface. By using NameInterface as the parameter’s type, you ensure that the method’s argument will have all the methods declared in NameInterface*"
### UML
==unified modeling language==: gives overall view of complex system more effectively thats a natural language or a programming language
- you can indicate the visibility of a field or method preceding its name with 
	- + for public
	- - for private
	- `#` for protected