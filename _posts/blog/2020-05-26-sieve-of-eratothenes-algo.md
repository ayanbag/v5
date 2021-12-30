---
layout: post
title: "Sieve of Eratosthenes Algorithm - the ancient algorithm"
author: "Ayan Bag"
categories: blog
tags: [algorithms]
image: 
---


**Sieve of Eratosthenes** is a simple and ancient algorithm to find thr prime number up to a given limit. This is one of the most efficient algorithm to find small prime numbers. This algorithm for collecting primes numbers is invented by Eratosthenes (276 - 194 BC).

**Time Complexity** of Sieve of Eratosthenes : O(n log(log n))

For the given value of n, the algorithm works iteratively making the multiples of primes as composite, starting from 2. Once all the multiple of 2 have been marked as composite, the multiple of the next prime, i.e 3 are marked composite. This process go on until

![955558e6ac3d6a1c1bc8d3c8b8534aca 1](https://user-images.githubusercontent.com/28982255/82886000-89298600-9f63-11ea-881d-8bf30b6c0eb7.png)


where p is a prime number.


### Working of Sieve of Eratosthenes Algorithm

Here in the algorithm, 0 is represent as a composite number.

- To find all the prime number up-to **n** , we have to generate a list of integers from **2 to n**. [Because the first and smallest prime number is 2]
- Initially, let p equal 2, the first prime number.
- Now we have to mark all the multiple of p which are less than n as composite, i.e replacing the number in the generated list with 0 **except p itself**.
- Assign the value of p to the next prime number.
- Repeat the process until 

![955558e6ac3d6a1c1bc8d3c8b8534aca 1](https://user-images.githubusercontent.com/28982255/82886000-89298600-9f63-11ea-881d-8bf30b6c0eb7.png)


When the algorithm terminates, all the numbers in the list that are not marked are prime.

![soe1](https://user-images.githubusercontent.com/28982255/82891130-deb56100-9f6a-11ea-8743-09d63deb4765.gif)


### Implementation with an Example

Problem :  Generate all the primes less than 11

Solution : 

```python 
import math
n = 200 # n is any arbitrary integer
List = []
for x in range(2, n): # add numbers from 2 to n - 1 to List
    List.append(x)
# note the above statement is equivalent to List = range(2, n)
p = 2 # p is a prime
while not int(math.sqrt(p)) + 1 > n: # continue to mark out primes until square root of p is less than n
    for x in range(p * 2, n, p): # remove all the multiples of p
        List[x - 2] = 0
    p += 1
    while p - 2 < len(List) and List[p - 2] == 0: # assign p to the next prime. Next prime is the next non zero number in the list
        p += 1
for x in List: # search for non zero or prime numbers in the list and print them
    if x != 0:
        print (x)
```



### Live Code

Try the above code


<iframe height="500px" width="100%" src="https://repl.it/@ayanbag/seive?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>











