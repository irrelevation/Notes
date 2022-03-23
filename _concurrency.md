## Reasons for Concurrency

* Improved perceived reaction time
* Improved Speed
* Improved modelling of concurrent real world situations

## Martelli Model of Scaleability

* 1 core: Single thread and single process
* 2-8 cores: Multiple Threads and Multiple Processes
* 9+ cores: Distributed Processes

The second category poses a problem: It is easy that the problem outscales our architecture and we can not simply jump to distributed processing.

## Threads vs Processes

Strength of Threads: Shared state, cheap communication, easy to implement, easy to learn the tools (locks and queues)
Weakness of Threads: Shared state, race conditions, overhead of thread management, Locks and Thread switches have a cost, hard to get right
Strength of Processes: No shared state, no race conditions, total independence
Weakness of Processes: No shared state, communication is expensive

## Async

Pros:
* maximises CPU utilisation because it has less overhead
Async switches cooperatively. Now you are responsible for managing switches, keywords are "yield" and "await". You need far fewer locks, makes it easier to get right. You have less overhead.
Switching tasks with Async is super cheap, in fact it takes less time than a regular function call. Under the hood async operates with generators. Those generators have persistent state. If you hand control back to a generator, the stack frame already exists. A function on the other hand, has to build up that state, before it can operate.

Cons:
* You can't do anything blocking
* Steep learning curve because it comes with a lot of new tools (futures, event loops, non-blocking versions of just about anything)

Pros:
* Way easier to get right than threads with locks, especially for complex systems

##Testing Threaded Code

#### Fuzzing
A Technique for amplifying race condition errors. Stretch the time of each of the steps of the program by putting in sleeps everywhere.

## Amdahl's Law
