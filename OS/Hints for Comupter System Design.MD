## Hints for Cmputer System Design
Butler W.Lampson


This paper talks about some aspects/trade-offs to think about when designing Computer system.  

### The most vague but most important hint is to obtain the right functionality for a system.  
Interface design must satisfy three things:  
* It should be simple 
* It should be complete, meaning normal and worst cases are considered
* It should admin a suggiciently small and fast implementation
  - Do one thing at a time and do it well
    1. When an interface undertakes too much it results in a large, slow, and complicated implementation. Service must have a fairly predictable cost and the interface must not promise more than the implementer knows how to deliver.
    2. some interfaces are ok to sacrifice performance for functionality.  
  - Get it right
    1. Do not generalize; generalization is generally wrong. It may produce buges that are hard to find.


##### Corollaries about simplicity and generalization:  
- Make it fast rather than powerful
	* if it's fast, the client can program the function it wants and another client can program some other functions. The trouble with slow, powerful operations is that the client who doesn;t want the poewer pays more for the basic function.

- Don't hide power
	* The purpose of abstraction is to conceal the undesired properties but desired ones shouldn't be hidden.
	* if a low level of abstraction allows something to be done quickly, it shouldn't be hidden by higher levels.
  
- Use procedure arguments to provide flexibility in an interface.
	* A good example of this is an enumeration procedure that returns a result set based on a certain property, The best interface would allow the client to pass their own filter to the enumeration procedure rather than fighting with built in mechanism.

- Leave it to the client
	* If it is cheap to pass control of an interface back and forth, the interface should just quickly solve some problem and leave the rest to the client.

### Continuity
##### Keep basic interfaces stable.  
Keep software interfaces stable since they are shared by more than one part of a system. If a system is programmed in a language without type-checking, its hard to change an interface, since its hard to track down its clients and checking for elementary incompatibilities. 

##### Keep a place to stand if you do have to change interfaces
Compatibility package, implements an old interface on top of a new system.
Word-swap debugger, writing the real memory of the target system onto a secondary storage device and reading in the debugging system in its place.


### Making implementations work
##### Plan to throw one away
Prototyping and testing/optimizing

##### Keep secrets of the implementation
Secrets are assumptions about an implementation that client programs are not allowed to make. In other words, they are things that can change; the interface defines the things that cannot change. Thus, it is easier to program and modify a system if its parts make fewer assumptions about each other. However, one way to improve performance is to increase the number of assumptions that one part of a system makes about another. Thus there is a trade-off.

##### Divide and conquer
We reduce hard problem to several easier ones to solve it.

##### Use a good idea again rather than generalizing it.(use the idea, not the code)
A specialized implementaion of the idea may be much more effective than a general one.

### Handling all the cases
##### Handle normal and worst cases separately.
the normal case must be fast, the worst case must make some progress. Must consider how to deal with the worest case.

### Speed
##### Split resources in a fixed way if in doublt, rather than sharing them.
It is usually faster to allocate dedicated resources, but this increases cost.

##### Use static analysis if you can
A program can read data much faster when the data is read sequentially. When in sequential order the data becomes predictable. However, it is verydifficult for a programmer to go over the code and optimize the disk transfers. This leads to Dynamic Analysis by demand paging which is at least as good.

##### Dynamic translation
Make translation easy, so it can be quickly interpreted is a nice change from bit to bit translation. Another idea of this scheme is to translate on demand and cache the result.

##### Use hints(cache) to speed up normal execution
Store information that takes a long time to compute. A cache must be true - invalidate the value and/or update the value.

##### When in doubt, use brute force.
BF is easier as the cost of the hardware comes down.

##### Compute in the background
When it is possible , computing in the background.

##### Batch processing
Doing things incrementally. Disks and tapes work better when accessed sequentially. Errors recovery is much simpler.

##### Safety first
In allocating resources, strive to avoid disaster rather than to attain an optimum. Its easy enough ot overload a system and drastically degrade the service.

##### Shed load
Do not let the system become overloaded, must take control. To shed load, an interactive system can refuse new users, or even deny service to existing ones; A memory manager can limit the jobs being served so that all their working sets fit in the available memory, etc..

### Fault Tolerance
##### End-to-end
Error recovery is absolutely necessary for a reliable system, and any other error detection or recovery is not logically necessary, but is strictly for performance.
Two pitfalls with the end-to-end strategy:
 * it requires a cheap test for success
 * it can lead to working systems with sever performance defects, which may bot be obvious until a opration is placed on heavy load.



##### log updates to record the truth about the state of an object
A log is a very simple data structure wich can be reliably written and read, and cheaply forced out on disk or other storage that can survive a crash. To use a log, record every update as alog entry, consisting of the name of the update procedure and its arguments. This allows the same statement from the log to be executed later.  
The update procedure must be a true function:
 * its result does not depend on any state outside its arguments;
 * I has no side effects, except on the object in whose log it appears.
The arguments must be values(immediate values). Value must be copied into the log entry.

##### Make actions atomic or restartable.
An atomic action is one which completes or has no effect. In most storage systems, fetch and store operations are atomic so either it cimpletely retrieves some arbitraty word or it doesn't. This eliminates the need for intermeidiate steps when attempting to revober from any errors.  
The advantages of atomic actions for fault-tolerance:
If a failure occurs during the action it has no effect, so that in recovering from a failure it is not necessary to deal with any of the intermediate states of the action.  
A log entry usually needs to be restartable. Which means that it can be partially executed any number of times before a complete execution, without changing the result.

  
   
     
  [ref:Hints for computer system design](https://dl.acm.org/citation.cfm?doid=800217.806614)
