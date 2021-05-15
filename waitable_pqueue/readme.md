# Waitable Priority Queue
A Waitable Priority Queue is an extension of a Java PriorityQueue<E<E>>, in which in addition to have a priority it is thread safe 

## Constructors
### WPQ has two constructors:
#### 1. WaitablePriorityQueue(int capacity)
  * Receives initial capacity
#### 2. WaitablePriorityQueue(int capacity, Comparator<E<E>> cmptor)
  * Receives initial capacity and Comparator function to be implemented by the user

## Main operations on Queue:
* **void enqueue(E item)** - Inserts a new element to a given pqueue, according to a given priority
* **E dequeue()** - Removes data from the start of a given pqueue
* **boolean remove(E element)** - Removes a single instance of the specified element from this queue, if it is present
* **int size()** - Returns the number of elements in this wpq
* **boolean isEmpty()** - Returns TRUE if the wpq is empty
