### [iOS Tech Interview](https://github.com/venvear/iOS-Tech-Interview/blob/master/README.md)

## Swift Method Dispatch

The goal of dispatch is for the program to tell the CPU where in memory it can find the executable code for a particular method call. Before we delve into how Swift behaves, let’s look at each of the three types of method dispatch one by one. Each one has tradeoffs between execution performance and dynamic behavior.

## Direct Dispatch
Direct dispatch is the fastest style of method dispatch. Not only does it result in the fewest number of assembly instructions, but the compiler can perform all sorts of smart tricks, like inlining code, and many more things which are outside of the scope of this document. This is often referred to as static dispatch.

However, direct dispatch is also the most restrictive from a programming point of view, and it is not dynamic enough to support subclassing.

## Table Dispatch
Table dispatch is the most common implementation of dynamic behavior in compiled languages. Table dispatch uses an array of function pointers for each method in the class declaration. Most languages refer to this as a “virtual table,” but Swift uses the term “witness table.” Every subclass has its own copy of the table with a different function pointer for every method that the class has overridden. As subclasses add new methods to the class, those methods are appended to the end of this array. This table is then consulted at runtime to determine the method to run.

## Message Dispatch
Message dispatch is the most dynamic method of invocation available. This is a cornerstone of Cocoa development, and is the machinery that enables features like KVO, UIAppearance, and Core Data. A key component to this functionality is that it allows developers to modify the dispatch behavior at runtime. Not only can method invocations be changed via swizzling, but objects can become different objects via isa-swizzling, allowing dispatch to be customized on an object-by-object basis.

When a message is dispatched, the runtime will crawl the class hierarchy to determine which method to invoke. If this sounds slow, it is! However, this lookup is guarded by a fast cache layer that makes lookups almost as fast as table dispatch once the cache is warmed up. But this just touches the surface of message dispatch. This blog post is a great deep dive in to all sorts of technical details.

