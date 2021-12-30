---
layout: post
title: "Understanding Linked List in Python"
author: "Ayan Bag"
categories: blog
tags: [data-structures]
image: 
---

**Linked List** is a list of elements (containing data) in which the elements are linked together. In other words, it is an ordered collection of elements. It differ from the list in the way we store elements. Unlike list, Linked List doesn't store its elements at contiguous memory locations.
In Linked List, each link contains a connection to another link. Linked List is the second most-used data structure after array.

### Important Concepts to understand Linked List :

Each elements of a Linked List is called a **node** , and every node has two different parts :
-  **Data** : It contains the value to be stored in the node.
-  **Next** : It is the reference to the next node in the list.



Typical Node structure :

![](https://user-images.githubusercontent.com/28982255/80274780-7caed500-86fa-11ea-947a-949467143f1b.png)



A linked list is composed of many nodes. The first node is always refers as **head** and its used as the starting point for any iteration through the list. The last node must have `next` reference pointing to **None** to determine the end of the list. 



Linked List representation :



![](https://user-images.githubusercontent.com/28982255/80275244-aa494d80-86fd-11ea-8a1a-a6738b6bee23.png)



### Practical Application of Linked List in Computer Science:

- Implementation of **Stacks** and **Queues**
- Implementation of **Graphs**
- Dynamic Memory Allocation
- Performing arithmetic operations on long integers
- Manipulation of Polynomials by storing constants in the node of Linked List
- Representing Parse Matrix



### Practical Application of Linked List in Real World:

- **Image Viewer** : Previous and Next Images are linked , hence can be accessed by next and previous button
- **Music Player** – Songs in music player are linked to previous and next song. you can play songs either from starting or ending of the list.



## Implementing Linked List in Python

Now its the time to implement some Linked List in Python

### How to Create a Linked List ?

A linked list is created by using node. Firstly, we create a node object and create an another class to use this node object. We will pass appropriate values through node object to point the next data elements. 

In the following program, we will create a linked list with four data elements :

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class CLinkedList:
    def __init__(self):
        self.headval = None

lt = CLinkedList()
lt.headval = Node("A")
e2 = Node("B")
e3 = Node("C")
e4 = Node("D")

# Link first Node to second node
lt.headval.nextval = e2

# Link second Node to third node
e2.nextval = e3

# Link third Node to fourth node
e3.nextval = e4
```


### How to Traverse a Linked List ?

Traversing a linked list means going through every single node of Linked List from `head` of the Linked List to the node which has `next` value pointing to None. Singly linked list can traversed in forward direction only starting from the first element.

In the following program, we will print the the value of next data element by assigning the pointer of the next node to current data element :

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class CLinkedList:
    def __init__(self):
        self.headval = None

    def listprint(self):
        printval = self.headval
        while printval is not None:
            print (printval.dataval)
            printval = printval.nextval

lt= CLinkedList()
lt.headval = Node("A")
e2 = Node("B")
e3 = Node("C")
e4 = Node("D")

# Link first Node to second node
lt.headval.nextval = e2

# Link second Node to third node
e2.nextval = e3

# Link third Node to fourth node
e3.nextval = e4

lt.listprint()
```

The output of the above code :
```
A
B
C
D
```



### How to insert a New Node ?

Depending upon the location where you want to insert an item , there are different ways to insert item in the linked list. 

#### Inserting at the beginning of the Linked List :

This involves pointing the next node of next data to the current head of the Linked List. As a result, the current head of the linked list will become the second data element and the new node becomes the head of the linked list.

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class CLinkedList:
    def __init__(self):
        self.headval = None

# Print the linked list
    def listprint(self):
        printval = self.headval
        while printval is not None:
            print (printval.dataval)
            printval = printval.nextval
    def AtBegining(self,newdata):
        NewNode = Node(newdata)
		# Update the new nodes next val to existing node
        NewNode.nextval = self.headval
        self.headval = NewNode

lt = CLinkedList()
lt.headval = Node("A")
e2 = Node("B")
e3 = Node("C")

lt.headval.nextval = e2
e2.nextval = e3

lt.AtBegining("Z")

lt.listprint()
```

The output of the above code :
```
Z
A
B
C
```



#### Inserting at the end of Linked List :

This involves pointing the next pointer of the current last node of the linked list to the new data. As a result, the current last node of the linked list becomes the second last node of the linked list and the new data node becomes the last node of the current linked list.

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class CLinkedList:
    def __init__(self):
        self.headval = None

# Function to add newnode
    def AtEnd(self, newdata):
        NewNode = Node(newdata)
        if self.headval is None:
            self.headval = NewNode
            return
        laste = self.headval
        while(laste.nextval):
            laste = laste.nextval
        laste.nextval=NewNode

# Print the linked list
    def listprint(self):
        printval = self.headval
        while printval is not None:
            print (printval.dataval)
            printval = printval.nextval


lt = CLinkedList()
lt.headval = Node("A")
e2 = Node("B")
e3 = Node("C")

lt.headval.nextval = e2
e2.nextval = e3

lt.AtEnd("Z")

lt.listprint()
```

The output of the above code :
```
A
B
C
Z
```



#### Inserting in between two Data Nodes :

This involves pointing the next pointer of the specific node to the new node. 

```python
class Node:
    def __init__(self, dataval=None):
        self.dataval = dataval
        self.nextval = None

class CLinkedList:
    def __init__(self):
        self.headval = None

# Function to add node
    def Inbetween(self,middle_node,newdata):
        if middle_node is None:
            print("The mentioned node is absent")
            return

        NewNode = Node(newdata)
        NewNode.nextval = middle_node.nextval
        middle_node.nextval = NewNode

# Print the linked list
    def listprint(self):
        printval = self.headval
        while printval is not None:
            print (printval.dataval)
            printval = printval.nextval


lt = CLinkedList()
lt.headval = Node("A")
e2 = Node("B")
e3 = Node("C")

lt.headval.nextval = e2
e2.nextval = e3

lt.Inbetween(lt.headval.nextval,"Z")

lt.listprint()
```

The output of the above code :
```
A
B
Z
C
```



### Removing  a Node from Linked List :

To remove a node from the Linked List , we need to traverse the the list until we find our target node. Then we will link the pointer of the previous node of the target node to the next node of the target node.

```python
class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None

class CLinkedList:
    def __init__(self):
        self.head = None

    def Atbegining(self, data_in):
        NewNode = Node(data_in)
        NewNode.next = self.head
        self.head = NewNode
		
# Function to remove node
    def RemoveNode(self, Removekey):

        HeadVal = self.head

        if (HeadVal is not None):
            if (HeadVal.data == Removekey):
                self.head = HeadVal.next
                HeadVal = None
                return

        while (HeadVal is not None):
            if HeadVal.data == Removekey:
                break
            prev = HeadVal
            HeadVal = HeadVal.next

        if (HeadVal == None):
            return

        prev.next = HeadVal.next

        HeadVal = None

    def LListprint(self):
        printval = self.head
        while (printval):
            print(printval.data),
            printval = printval.next


llist = CLinkedList()
llist.Atbegining("A")
llist.Atbegining("B")
llist.Atbegining("C")
llist.Atbegining("D")
llist.RemoveNode("B")
llist.LListprint()
```

When the above code is executed, it produces the following result:
```
A
C
D
```



