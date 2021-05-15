# ThreadPool
A thread pool is a software design pattern for achieving concurrency of execution in a computer program. A thread pool maintains multiple threads waiting for tasks to be allocated for concurrent execution by the supervising program. By maintaining a pool of threads, the model increases performance and avoids latency in execution due to frequent creation and destruction of threads for short-lived tasks.

## API
* **submit**: all the submit methods creates TASK with functionality + priority 
     and push it to the WPQ
     1. **<<T>T> Future<<T>T> submit (Runnable taskToRun, Priority taskPriority)**
     2. **<<T>T> Future<<T>T> submit (Runnable taskToRun, Priority taskPriority, T result)**
     3. **<<T>T> Future<<T>T> submit (Callable<<T>T> taskToCall)**
     4. **<<T>T> Future<<T>T> submit (Callable<<T>T> taskToCall, Priority taskPriority)**
     * **NOTE**: A Runnable does not return a result and cannot throw a checked exception

* **void execute (Runnable taskToRun)** - Like **submit** but doesn't return Future<<T>T>
* **void setNumOfThreads(int threadsNum_set)** - Gives the user the ability to change the number of threads during runtime
* **void pause()** - Postponing the threadpool's activity
* **void resume()** - Return the threadpool to activity
* **void shutdown()** - Prevent the threadpool from receiving new activities, and close it
* **awaitTermination** - Waiting for the shutdown to end, and prevent from the main thread to continue up until the threadpool is completely closed
   * **void awaitTermination()** - With no time limitation
   * **void awaitTermination(long timeOut, TimeUnit measurementUnit)** - Gives the user the option to decide on a time limitation

## Inner Properties
* Based on [Waitable Priority Queue](https://github.com/itay-adi/ThreadPool/tree/main/waitable_pqueue)
* The user defines the initial number of threads, and can change it at run time
* Usage of the Executor Interfaces which supports launching new tasks
* Usage of Task<> as a wrapper for the assignments the user is pushing
* The treads will work immediately
* Each Submit returns a Future
  *  A Java Future represents a handler for each of the Tasks which gives info regarding its state and in some conditions can control it

## Inner Classes
* **private class Task<T> implements Comparable<Task<?>>**
   * Each Runnable/Callable the user is pushing into the threadpool with submit/execute, turns to a Task which can be compared to other tasks in order to map its 
   * inside Task we can find **private class TaskFuture implements Future<<T>T>**
      * TaskFuture is what that is been returned by submit, and can give info like:
         * boolean isCancelled() - Is Task cancelled
         * boolean isDone() - Is Task Done
         * T get() - Task's result
         * T get(long timeout, TimeUnit timeUnit) - Task's result (with time limit)
