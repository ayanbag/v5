---
layout: post
title: "What is A-Star Algorithm ?"
author: "Ayan Bag"
categories: journal
tags: [algorithms]
image: 
---


**A-Star Algorithm** is one of the most popular computer algorithm widely used in Path-finding and Graph Traversal. This algorithm efficiently search and plots a path between multiple nodes, or points, on the graph. It is used in various applications, such as *Maps*.

Peter Hart, Nils Nilsson and Bertram Raphael of Stanford Research Institute (now SRI International) first published the algorithm in 1968. It can be seen as an extension of Edsger Dijkstra's 1959 algorithm. 

**A-Star** achieves better performance by using heuristics to guide its search. For example, on a map with many obstacles, path-finding from points **A-Star* to **A-Star* can be difficult. A robot, for instance, without getting much other direction, will continue until it encounters an obstacle. With **A-Star **, a robot would instead find a walkable path.

### Why A-Star Algorithm ?

**A-Star** is based on using heuristic method to achieve optimality and completeness, and based the Best-First Algorithm.

When a search algorithm has the property of optimality, it means it is guaranteed to find the best possible solution. When a search algorithm has the property of completeness, it means that if a solution to a given problem exists, the algorithm is guaranteed to find it.

Each time **A-Star** enters a state, it calculates the cost, f(n) (n being the neighboring node), to travel to all of the neighboring nodes, and then enters the node with the lowest value of f(n).

The values are calculated with the following formula :

![](https://user-images.githubusercontent.com/28982255/85195754-ca0e8380-b2f2-11ea-90c6-e9489433da15.png)

where

- **g(n)** = the value of the shortest path from the start node to node n
- **h(n)** = a heuristic approximation of the node's value

The efficiency  is highly dependent on the heuristic value h(n), and depending on the type of problem, we may need to use a different heuristic function for it to find the optimal solution.

To understand the usage of the formula, we have to look at how the algorithm works.

*  Initialize the open list
*  Initialize the closed list put the starting node on the open list (you can leave its f at zero)
*  while the open list is not empty
    - find the node with the least **f** on the open list, call it "q"

    - pop q off the open list
    
    - generate q's 8 successors and set their parents to q
    
    - for each successor
      
        1. if successor is the goal, stop search successor.**g** = q.**g** + distance between successor and q 
        
           successor.**h** = distance from goal to successor   
    
           successor.**f** = successor.**g** + successor.**h**
    
        2. if a node with the same position as successor is in the OPEN list which has a lower **f** than successor, skip this successor

    	3. if a node with the same position as successor  is in the CLOSED list which has a lower f than successor, skip this successor otherwise, add  the node to the open list end (for loop)
       
   - push q on the closed list end (while loop) 

### Heuristic

To calculate the value of **h**, we can do two things :

- Calculate the exact value of **h** (Time Consuming method), OR
- Approximate the value of **h** using some heuristics (Less Time Consuming)

**Exact Heuristics - **

To calculate the exact value of **h** , firstly we have to pre-compute the distance between each pair of cells before running **A-Star ** algorithm.

If there are no blocked cells, then we can just find the exact value of **h** without any pre-computation using Distance Formula.

** Approximation Heuristics - **

There are three approximation heuristics to calculate **h** :

1. **Manhattan Distance** 

It is the sum of absolute values of differences in the goal’s x and y coordinates and the current cell’s x and y coordinates respectively, i.e.

```
h = abs (current_cell.x – goal.x) + abs (current_cell.y – goal.y) 
```
This type of heuristic is used, only when we allowed to move in four direction.

2. **Diagonal Distance**

It is the maximum of absolute values of differences in the goal’s x and y coordinates and the current cell’s x and y coordinates respectively, i.e.,

```
 h = max { abs(current_cell.x – goal.x), abs(current_cell.y – goal.y) } 
```

It is used only when we are alowed to move in **eight** direction only.

3. **Euclidean Distance**

It is the distance between the current cell and the goal cell using the distance formula.

```
h = sqrt ( (current_cell.x – goal.x) ^ 2 + (current_cell.y – goal.y) ^ 2 ) 
```

It is used when we are allowed to move in **all** direction.

**Dijkstra is a special case of A-Star Search Algorithm, where h = 0 for all nodes.**

