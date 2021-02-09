## iOS Tech Interview > Swift > Classes and Structs

Class and Structure
First, let’s take a look at what **classes** and **structs** have in common:

* They can define properties to store values, and they can define functions
* They can define subscripts to provide access to values with subscript syntax
* They can define initializers to set up their initial state, with init()
* They can be extended with extension (this is important!)
* They can conform to protocols, for instance to support Protocol Oriented Programming

**Classes** support a few more capabilities that structs don’t have:

* Classes can inherit from another class, like you inherit from UIViewController to create your own view controller subclass
* Classes can be deinitialized, i.e. you can call a function before the class is destroyed
* Classes are reference types and structs are value type

