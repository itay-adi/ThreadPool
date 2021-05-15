# ThreadPool
A thread pool is a software design pattern for achieving concurrency of execution in a computer program. A thread pool maintains multiple threads waiting for tasks to be allocated for concurrent execution by the supervising program. By maintaining a pool of threads, the model increases performance and avoids latency in execution due to frequent creation and destruction of threads for short-lived tasks.

## Inner Properties
* Based on [Waitable Priority Queue](https://github.com/itay-adi/ThreadPool/tree/main/waitable_pqueue)
* The user defines the initial number of threads, and can change it at run time
* Usage of the Executor Interfaces which supports launching new tasks
* Usage of Task<> as a wrapper for the assignments the user is pushing
* Each Submit returns a Future
  *  A Java Future represents the result of an asynchronous task
*  The treads will work immediately

## API
* submit: all the submit methods creates TASK with functionality + priority 
     and push it to WPQ 
