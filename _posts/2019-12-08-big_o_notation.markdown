---
layout: post
title:      "Big O Notation"
date:       2019-12-09 00:36:42 +0000
permalink:  big_o_notation
---


This is a concept I first encountered when I started to prepare for interviews, and to be honest, it took me a while to fully understand. 
I wanted to write about it because it pops up a lot in code challenges, and also as programmers, it is important to understand how we can improve our code, especially when it is a part of a large scale application. 

**So why big O?**

First let's look at the definition of Big O according to Wikipedia:

> Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity - Wikipedia

Mmm.. what does that mean you might be asking yourselves?...

Basically this means that we use big O to determine whether an algorithm will perform well given a large data set.
When we write a function and test it with different inputs, it might work well, but we need to take into consideration that as our code grows and becomes more complex, the input can grow and become larger which can significantly slow the execution of our functions, and our code in general. This is where big O comes in.
Implementing Big O helps to make sure we are using the best and most optimal algorithms to execute different tasks by calculating time complexity and space complexity. 

**Time Complexity** is the time it takes for a task to complete all its steps when executed.  
**Space Complexity** is how much space in memory we use to execute a task.

Usually there is a trade off between the optimal runtime and space used to execute an algorithm. Using more space in memory can help the algorithm run faster, while saving space in memory can cost more in terms of the algorithm speed. 

In deciding between the two, it depends what is more important to us in our application, do we have enough space and can afford using it to enhance the speed of our code, or are we writing code for a small device like a smartwatch and need to save as much space as possible?

**Time Complexity Overview:** 

*1. Constant time - O(1)*

O(1) means our code has one task to execute, it takes a constant time to run, for example:

```
def first_element(array)
  puts(array[0])
end

```
In this example the method prints out the first element of a given array. No matter what the size of the input, it will execute exactly one time. 

```
def first_element(array)
  puts(array[0])
	puts(array[1])
end
```
What about here? 
The runtime is now O(2), because the function has two steps. However, the runtime is still constant, so we can say it's O(1). Again, no matter what is the size of the array, the function will run a fixed number of times, so the runtime in constant. 

*2. Linear Time - O(n)*

Linear time complexity means that the function's execution time grows linearly as the input grows. 

```
def print_element(array)
  array.each {|i| puts(i)}
end
```
In this example, we are iterating over the array and printing each element. As opposed to the previous example, here the number of steps in the function change according to the size of the array. If the array has 5 elements, the function will execute 5 times, if the array has one million elements, it will execute a million times. As the input grows, so does the runtime, and it grows linearly. 

*3. Quadratic Time - O(n^2)*

In quadratic time, the time it takes to execute a function grows n^2 as the input grows.  
Usually we use this runtime in nested loops. 

```
def multiply_all_elements(array)
  array.each do |i| # o(n)
	   array.each do |j| # o(n)
			 i*j
		end
	end
end
```
In this example we are iterating over the array and for each iteration we are iterating over the whole array again. If we have n items in the array, the code will execute n* n times, which is n^2. 

*4. Logarithmic Time- O(log n) *

To understand logarithmic runtime, let's think about binary search.Binary search allows us to cut each step of the search by half. So unlike linear search, in which we need to check every item in an array, with binary search we can find an item of a million size array  in only 19 steps(!!!)

*5.Exponential Time- O(2^n)* 

The exponential growth is the opposite of the logarithmic growth. This type of algorithm is not very scalable, as the input grows it will run slow pretty soon. 
 
**Fast to Slow Runtimes:**

O(1) --> O(log n) --> O(n) --> O(n log n) --> O(n^2) --> O(2^n)

