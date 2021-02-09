### [iOS Tech Interview](https://github.com/venvear/iOS-Tech-Interview/blob/master/README.md)

## Strong, weak and unowned

The purpose of a **strong** reference is to keep an object alive. Strong referencing might result in several non-trivial problems [2]:
Retain cycles. Considering that Swift language is not cycle-collecting, a reference R to an object which holds a strong reference to the object R (possibly indirectly), results in a reference cycle. We must write lots of boilerplate code to explicitly break the cycle.
It is not always possible to make strong references valid immediately on object construction, e.g. with delegates.

**Weak** references address the problem of back references. An object can be destroyed if there are weak references pointing to it. A weak reference returns nil, when an object it points to is no longer alive. This is called zeroing.

**Unowned** references are different flavor of weak, designed for tight validity invariants. Unowned references are non-zeroing. When trying to read a non-existent object by an unowned reference, a program will crash with assertion error. They are useful to track down and fix consistency bugs.

`Swift Runtime represents every dynamically allocated object with **HeapObject** struct. It contains all the pieces of data which make up an object in Swift: reference counts and type metadata.`

## ARC and MRC

Automatic Reference Counting (**ARC**) is Swift’s system of tracking memory you’re using. When you create an object from a class, Swift remembers that instance is being referenced precisely once. If you then point another variable at that object, Swift will increment the reference count to 2, because two variables are pointing at the same object. If you now destroy the first variable (perhaps it was inside a function and that function ended), Swift takes the reference count back down to 1.

All this matters because as long as the reference count is greater than 1 the object stays alive. But when the final variable referencing that object goes away, Swift will take the reference count down to zero. As no existing variables point at the object, its RAM can be released. So, ARC is a way of tracking an object’s lifetime efficiently, and for the most part you don’t even notice it happens – Swift does all the work for you.



## Memory leak and retain cycle

A memory leak is a type of resource leak that occurs when a computer program incorrectly manages memory allocations in such a way that memory which is no longer needed is not released. In object-oriented programming, a memory leak may happen when an object is stored in memory but cannot be accessed by the running code.


[more](https://doordash.engineering/2019/05/22/ios-memory-leaks-and-retain-cycle-detection-using-xcodes-memory-graph-debugger/#:~:text=I.,strong%20references%20to%20each%20other.
)


[more](https://medium.com/mackmobile/avoiding-retain-cycles-in-swift-7b08d50fe3ef)
