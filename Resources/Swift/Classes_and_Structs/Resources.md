## iOS Tech Interview > Swift > Classes and Structs

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



