### [iOS Tech Interview](https://github.com/venvear/iOS-Tech-Interview/blob/master/README.md)

## Reference and Value types

**Value types** are stored directly where the computation goes. Each variable of value type has its own copy of data and operations on one do not affect the other.

**Reference types** are stored somewhere else and we have a reference pointing to that place in memory.
Variables of reference type can point to the same data; hence operations on one variable can affect the data pointed by the other variable.

***Which is faster among Value Types and Reference Types?***

* **Value types** are faster than Reference types, because.
Value Types are stored on Stack Memory. Variables allocated on the stack are stored directly to the memory and access to this memory is very fast, and its allocation happens during compilation. When a function creates a variable, the stack stores that variable and is destroyed automatically when the function exits.
* **Reference Types** are stored on Heap Memory. Heap is more dynamic but less efficient than the stack. The heap doesn’t automatically destroy its object, It has to be handled externally. In swift ARC is used to handle this. In ARC, the reference count of an object is tracked and once count becomes zero, the object is deallocated. This overall process of allocation, tracking the references and deallocation makes heap slower compared to stack.

> * For reference types, the objects are stored on the heap, while their pointers are stored on the stack. For value types, the object itself is stored on the stack.
> * In case a value stored on a stack is captured by a closure, that value will be moved to the heap so that it’s available till the closure is executed.
> * If the value type is part of a class, the value is stored in the heap along with the class instance.
> * Reference types are always saved in the Heap, whereas Value Types always go where they are declared.


## Stack and Heap

### Stack
The stack is a region of memory which contains storage for local variables, as well as internal temporary values and housekeeping. On a modern system, there is one stack per thread of execution. When a function is called, a stack frame is pushed onto the stack, and function-local data is stored there. When the function returns, its stack frame is destroyed. All of this happens automatically, without the programmer taking any explicit action other than calling a function.

### Heap
The heap is, essentially, everything else in memory. (Yes, there are things other than the stack and heap, but let's ignore that for this discussion.) Memory can be allocated on the heap at any time, and destroyed at any time. You have to explicitly request for memory to be allocated from the heap, and if you aren't using garbage collection, explicitly free it as well. This is where you store things that need to outlive the current function call. The heap is what you access when you call malloc and free.

[more](https://www.mikeash.com/pyblog/friday-qa-2010-01-15-stack-and-heap-objects-in-objective-c.html)

## Classes and Structures


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

