### [iOS Tech Interview](https://github.com/venvear/iOS-Tech-Interview/blob/master/README.md)


## GCD

Grand Central Dispatch (GCD) is a low-level API for managing concurrent operations. It can help you improve your app’s responsiveness by deferring computationally expensive tasks to the background. It’s an easier concurrency model to work with than locks and threads.

GCD is built on top of threads. Under the hood it manages a shared thread pool. With GCD you add blocks of code or work items to dispatch queues and GCD decides which thread to execute them on.

Queues
As mentioned before, GCD operates on dispatch queues through a class aptly named DispatchQueue. You submit units of work to this queue and GCD will execute them in a FIFO order (First In, First Out), guaranteeing that the first task submitted is the first one started.

Dispatch queues are thread-safe which means that you can access them from multiple threads simultaneously. The benefits of GCD are apparent when you understand how dispatch queues provide thread safety to parts of your own code. The key to this is to choose the right kind of dispatch queue and the right dispatching function to submit your work to the queue.

Queues can be either serial or concurrent. Serial queues guarantee that only one task runs at any given time. GCD controls the execution timing. You won’t know the amount of time between one task ending and the next one beginning:

Concurrent queues allow multiple tasks to run at the same time. The queue guarantees tasks start in the order you add them. Tasks can finish in any order and you have no knowledge of the time it will take for the next task to start, nor the number of tasks that are running at any given time.

[more](https://www.raywenderlich.com/5370-grand-central-dispatch-tutorial-for-swift-4-part-1-2)

## NSOperation

NSOperation adds a little extra overhead compared to GCD, but we can add dependency among various operations and re-use, cancel or suspend them.
NSOperationQueue, It allows a pool of threads to be created and used to execute NSOperations in parallel. Operation queues aren’t part of GCD.
NSBlockOperation allows you to create an NSOperation from one or more closures. NSBlockOperations can have multiple blocks, that run concurrently.

[more](https://nshipster.com/nsoperation/)

## RunLoop

Run Loop is a mechanism that allows threads to process events at any time without exiting.
Run Loop is actually an object that manages the events and messages that it needs to process and provides an entry function to execute the logic of the Event.

After the thread executes this function, it will stay in the “accept message-> wait-> processing -> Sleep till next message -> accept message” loop inside the function until the end of the loop (such as a message passed to quit) and the function returns.

In OSX / iOS, We have NSRunLoop and CFRunLoopRef for same purpose. CFRunLoopRef is inside the CoreFoundation framework. It provides APIs for pure C functions, all of which are thread-safe.
NSRunLoop is a wrapper based on CFRunLoopRef that provides object-oriented APIs, but these APIs are not thread-safe.

The system has 5 modes registered by default:
kCFRunLoopDefaultMode: App’s default mode, usually the main thread runs in this mode.
UITrackingRunLoopMode: Interface tracking mode, used for ScrollView to track touch and slide, to ensure that the interface is not affected by other modes when sliding.
UIInitializationRunLoopMode: The first mode that is entered when the app is started, it will not be used after the startup is complete.
GSEventReceiveRunLoopMode: Internal Mode for receiving system events, usually not used.
kCFRunLoopCommonModes: This is a placeholder mode and has no practical effect.

Four functions of Run Loop:
Keep the program running and accept user input
Decide when events should be handled by the program
Call decoupling
Save CPU time

The run loop of the main thread is started by default. In an iOS application, after the program starts, there will be a main() function as follows:

The key point is the UIApplicationMain() function. This method will set an NSRunLoop object for the main thread.

[more](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/RunLoopManagement/RunLoopManagement.html)

## Synchronization

[more](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/ThreadSafety/ThreadSafety.html)

## Problems

[more](https://austingwalters.com/multithreading-common-pitfalls/)

### Race condition

[more](https://developer.apple.com/library/archive/documentation/Security/Conceptual/SecureCodingGuide/Articles/RaceConditions.html)

### Deadlock

[more](https://www.cocoawithlove.com/2010/06/avoiding-deadlocks-and-latency-in.html)

### Readers–writers problem

[more](https://medium.com/@oyalhi/dispatch-barriers-in-swift-3-6c4a295215d6)

[more](https://en.wikipedia.org/wiki/Readers%E2%80%93writers_problem)

