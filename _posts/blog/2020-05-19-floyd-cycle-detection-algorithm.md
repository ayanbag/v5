---
layout: post
title: "Floyd Cycle Detection Algorithm"
author: "Ayan Bag"
categories: journal
tags: [algorithms]
image: 
---


### What is Loop in Linked List ?

Generally, the last node of a Linked List points to **null**, which indicates that it is end of the list. But when there is a loop in a Linked List , the last node points to some of the interval node or first node or itself. In this case with we traverse a Linked List node one by one, our traversal will never end as it is in loop

![Loop in Linked List](https://user-images.githubusercontent.com/28982255/82292403-7a255f80-99c8-11ea-805c-2279f6544dd6.png)


### Detection of Loop in Linked List

There are many ways for detecting any cycle in linked list, **Floyd Cycle Detection Algorithm** works better than other in terms of Time Complexity and Space Complexity. It is a pointer algorithm which uses only two pointers, which moves through the sequence. It is also called "tortoise and the hare algorithm".

- **Space Complexity of Floyd Cycle Detection Algorithm :** O(1)
- **Time Complexity of Floyd Cycle Detection Algorithm :** O(n)

### Working of Floyd Cycle Detection Algorithm and its Mathematical Proof

The logic of this algorithm can be illustrated as a race between a hare and a tortoise. Hare is always faster than a tortoise and it will always win the race against tortoise unless their is a cycle in the race track. If it exists in the race track, race will continue forever and hare will see tortoise again and again.

Lets understand with the help of experiment :


<p style="text-align:center;"><img src="https://user-images.githubusercontent.com/28982255/82298242-76e2a180-99d1-11ea-9dae-33449dcbbe0e.png" alt="floyd cycle detection"></p>

- Assuming the distance between the beginning node or head node of Linked List and starting node of the loop is **a**
- Assuming the distance between the starting node of the loop and meeting node of *hare* and *tortoise* is **b**
- Assuming the distance between the meeting node of *hare* and *tortoise* and starting node  of the loop is **c**

Tortoise moves one node at a time and the hare moves two node at same time. So, we can say when the tortoise has moved distance **d** , then turtle has moved pointer **2d**.

```latex
So the length of the loop is b+c

When both tortoise and hare meets, tortoise covers a distance d = a+b and
hare covers a distace 2d = (a+b+c+b)

Therefore,
2*d = (a+b+c+b)
d = (a+b)

Now,
=> 2*d = 2*(a+b)
=> 2*(a+b) = (a+b+c+b)
=> 2*a + 2*b = a+2*b+c
=> a=c

It means distance from head node to the start of loop node is same as distance between meeting point of the tortoise and hare to the starting node of loop
```

So this shows after getting meeting point, if one pointer is placed at the beginning of the list, then moving both pointer one node at a time then they will meet at the start of loop.



### Implementation of Floyd Cycle Detection Algorithm

Implementation in **Python**  

```python

# Node class
class Node:
    # Constructor to initialize the node object
    def __init__(self, data):
        self.data = data
        self.next = None
class LinkedList:
    # Function to initialize head
    def __init__(self):
        self.head = None
    # Function to insert a new node at the beginning
    def push(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node
    # Utility function to print it the linked LinkedList
    def printList(self):
        temp = self.head
        while(temp):
            print (temp.data,)
            temp = temp.next
    def detectLoop(self):
        slow_p = self.head
        fast_p = self.head
        while(slow_p and fast_p and fast_p.next):
            slow_p = slow_p.next
            fast_p = fast_p.next.next
            if slow_p == fast_p:
                print ("Found Loop")
                return
# Driver program for testing
llist = LinkedList()
llist.push(20)
llist.push(4)
llist.push(15)
llist.push(10)
# Create a loop for testing
llist.head.next.next.next.next = llist.head
llist.detectLoop()
```
Output :
```
Found Loop
```





### Live Code 

Try the above code

<iframe height="500px" width="100%" src="https://repl.it/@ayanbag/floyd-cycle-detection?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

