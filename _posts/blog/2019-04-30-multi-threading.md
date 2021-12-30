---
layout: post
title: "Introduction to Multi-threading in Python"
author: "Ayan Bag"
categories: journal
tags: [python]
image: 
---


Like multiprocessing, multithreading is a way of achieving multitasking. Most of the code we write in Python is single threaded. A python virtual machine runs behind the scene uses a thread called the **main thread** i.e `main()` to execute the code which has written.

A **thread** is an entity within a process that can be scheduled for execution. Also, it is the smallest unit of processing that can be performed in an OS (Operating System). In simple words, a **thread** is a sequence of such instructions within a program that can be executed independently of other codes.

**Multithreading** is defined as the ability of a processor to execute multiple threads concurrently.

### Why use Multithreading?

To make the best use of the underlying processor and to improve the performance of our application, we can create multiple threads that can execute in parallel making the best use of processor and also our application will give the best user experience, it will be very fast.

### Way to create Multithreading :

To create multiple threads in our application, we have three ways :

* To use a function: We will define a function just like we define our function. Now we will create an object of type thread.

    t=Thread(target=functionName,args)

To the object, we will pass the target which is the function we have created, the name of the function and the second argument here is the argument to the function. After we invoke t.start() i.e.

    t=Thread(target=functionName,args)
    t.start()

When we do that the Python Virtual Machine will create a new thread that will run in parallel with the **main **thread and as a part of the thread the code within this function will be executed and the arguments are passed to the function.

* By extending the thread class:

We will import the Threading Module and extend the thread class. And the second step is to override the run method.

* Without extending the thread class:(**Hybrid Approach**)

In this method, we will create a class and also add function we want within that class and also add function we want within that class, but the class doesn’t extend the Thread Class. Instead, we will create an instance of the thread then we will pass myobj.display , the function which we to execute within the object as the target and the arguments in the second parameters.

    class MyThread:
           display() #function we want to create
    t=Thread(target = obj.display,args)
    t.start()

## Main Thread

Behind the scenes, when we run our Python programs so far which is being single threaded, there was a **main thread** that was being created by the Python interpreter that represents our program.

To get the information on the main thread :

    import threading
    print(threading.current_thread().getName())

Output: Main Thread

where, **current_thread()** : gives info about current thread, and **getName()** : to get the name of the current thread.

Also to print the current thread name use the command : current_thread().getName()

## Thread using a function

We are going to create a function that will display the number from 0 to 10 and then we will spawn that function off a thread of its own.
```
    from threading import Thread
    def display_Number():
       i=0
       while(i<=10):
         print(i)
         i+=1
    #**Now to spawn this function as a thread
    **t=Thread(target= display_Number)

    #**To start the Thread
    **t.start()
```
Output:
```
    0
    1
    2
    3
    .
    .
    10
```
Now the thread is no longer the main thread. The output is from a thread of its own.

## Thread extended the Thread Class

We are going to extend a superclass called *Thread *and override the run method inside.

    from threading import Thread
    Class MyThread(Thread):
         def run(self):
              i=0
              while(i<=10):
                   print(i)
                   i+=1
    t=MyThread()
    t.start() #**It is spawn of a new thread and invoke the run method
               that we have overridden**

Creating a thread using a class :

    from threading import *
    class MyThread:
          def display_Number(self):
                i=1
                while(i<=10):
                    print(i)
    obj=MyThread() #**Object of our class MyThread
    **t=Thread(target=obj.display_Number)
    t.start

Output:

    1
    2
    .
    .
    10

## Multi-Threading in Action

To create a multithreading application, we have different thread objects.

    from threading import Thread
    class MyThread:
          def display_Number(self):
              i=0
              while(n<=10):
                   print(i)
                   i+=1

    obj=MyThread()

    #**Starting Thread 1
    **print("Thread 1")**
    **t=Thread(target=obj.display_Number)
    t.start()

    #**Starting Thread 2
    **print("Thread 2")
    t2=Thread(target=obj.display_Number)
    t2.start()

    #**Starting Thread 3
    **print("Thread 3")**
    **t3=Thread(target=obj.display_Number)
    t3.start()

Output:

    Thread 1
    0
    1
    2
    3
    4
    Thread 2
    0
    1
    2
    3
    4
    5
    6
    Thread 3
    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10

**Note: **The scheduling of these threads is up-to-the thread scheduler.

Here in the above example, the Thread 1 prints from 0 to 4, then Thread 2 starts off. It depends on the Python thread scheduler. But all of them will do this work at the end. If we re-run the program could be totally different.

Output:

    Thread 1
    1
    2
    ..
    10
    Thread 2
    1
    2
    3
    ..
    10
    Thread 3
    1
    2
    3
    ..
    10

## Thread Synchronisation

When multiple threads are accessing the same resources it is very important that it doesn’t corrupt each other resources or objects. For example: Booking tickets for films.

![](https://cdn-images-1.medium.com/max/2000/1*-xTvcw3icjnKczpZCk0HzQ.png)

So that two different users never end up buying the same tickets or the same seats due to **Thread Synchronisation**.

Thread synchronization is defined as a mechanism that ensures that two or more concurrent threads do not simultaneously execute some particular program segment known as **Critical section**. And Critical section is referred to the parts of the program where the shared resource is accessed*.*

We can lock an object for a particular thread using two different ways, using ***Locks*** or ***Semaphores***.

### Locks

Locks are the most fundamental synchronization mechanism provided by the **threading** module. Locks can be held by a single thread, or by no threads at all. If a thread attempts to hold a lock that’s already held by some other thread, execution of the first thread is halted until the lock is released.

Generally, Locks are used to synchronize access to shared resources. For each shared resource, we have to create a **Lock** object. When you need to access the resource, call **acquire** to hold the lock, and call **release** to release it:

    lock = Lock()

    lock.acquire() *# it will block if resources are already held*
    ... access shared resources
    lock.release()

For proper functioning, we need to use** try-finally **so that** **the lock releases even if something goes wrong when accessing the resource.

    lock.acquire()
    try:
       ...access shared resources
    finally:
       lock.release() *# release lock, no matter what*

### Semaphores

A semaphore is a more advanced lock mechanism. A semaphore is based on an internal counter which is decremented each time acquire() is called and incremented each time release() is called. If the counter is equal to 0 then acquire() blocks. It is the Python implementation of the Dijkstra semaphore concept: P() and V(). Using a semaphore makes sense when you want to control access to a resource with limited capacity like a server.

Here is a simple example:

    semaphore = threading.BoundedSemaphore()
    semaphore.acquire() *# decrements the counter*
    ... access the shared resource
    semaphore.release() *# increments the counter*

## Advantages and Disadvantages of Multi-Threading

### Advantages

* It doesn’t block the user. This is because threads are independent of each other.

* Parallelize tasks

* Enhanced performance on multi-processor machines.

* Multi-threaded servers and interactive GUIs use multithreading exclusively

### Disadvantages

* Difficult to debug, the result is sometimes unpredictable

* As the number of threads increases, complexity increases

* Potential deadlocks lead to **starvation **i.e some threads may not be served with a bad design

* Constructing and synchronizing threads are CPU/memory intensive.

