
Q: What is the motivation for needing a new scheduler?  
A: Existing priority-based schedulers give poor control over relative computation rates. Its difficult to adjust priorities to get fairness or fixed ratio.  

Q: What are the goals of a lottery scheduler?  
A: Give proportional-share resourse management and provide a modulaxity design.

Q: What are teh advantages of using lottery tickets to represnet resource rights?  
A:  
 * abstract (no machine details)
 * relative (fraction of resources-> more if lightly loaded)
 * uniform (can be used for different resources- cpu, mem, disk)  
   
Q: How is scheduling decision made? What is the expectation for which process will be scheduled?Does lottery scheduling need to do anything special to guard against starvation?  
A: Hold a lottery- winner gets scheduled. Probabilistically fair, probablity of winning is t/T. Starvation problem is solved by use MLFQ.


Q: how does one implement a lottery? What are ways to optimize the search for the winner?  
A: Fast random number generator that generates number from 0 to n-1 (n is the number of active tickets, same as the jobs on ready queue)
