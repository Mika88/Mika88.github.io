---
layout: post
title:      "Array Methods You Might Have Missed"
date:       2018-12-15 22:03:16 -0500
permalink:  array_methods_you_might_have_missed
---

Initially I was going to do an array iteration cheat sheet and go over all the different methods in terms of their return values and main uses to help me remember them better.
Then, I started going over all the array methods in Ruby docs and realized there are a number of methods I never used before and thought it might be nice to go over these methods and create a cheat sheet that contains these 'new' methods. 

So here they are, with a short explanation and examples: 

* **#assoc(obj) and #rassoc(obj)**
    These methods take in an object as an argument and by searching through an array, that its elements are also             arrays,  compare the object to the elements in the nested arrays using obj==. 
	assoc(obj) compares the given object with the first element in each nested array, while  rssoc(obj) compares the object with the second element. Both methods return the first array that matches the object. 
For example:
 
   ```
   a = [ [ 1, "one"], [2, "two"], [3, "three"], ["ii", "two"] ]
	
   a.assoc(3) # =>  [3, "three"]
   a.rassoc("two")    #=> [2, "two"]
   a.rassoc("four")   #=> nil
	 
   ```

*  **#at(index)**
   Takes in an argument of an index and returns the element in the given index position. 
	 If the argument given is a negative index, it counts the index from the end of the array.
   
   ```
   a = [ "a", "b", "c", "d", "e" ]
   a.at(0)     #=> "a"
   a.at(-1)    #=> "e"
  ```
	
*   **#bsearch** 
Uses a binary search and finds the first element that matches the condition inside a given block.

 ```
 ary = [0, 4, 7, 10, 12]
 ary.bsearch {|x| x >=   4 } #=> 4
 ary.bsearch {|x| x >=   6 } #=> 7
 ary.bsearch {|x| x >=  -1 } #=> 0
 ary.bsearch {|x| x >= 100 } #=> nil
 ```
   
* **#combination(n)**
  When invoked on an array, returns all the different combinations by the length of *n*. 
	
 ```
 a = [1, 2, 3, 4]
 a.combination(1).to_a  #=> [[1],[2],[3],[4]]
 a.combination(2).to_a  #=> [[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]
 a.combination(3).to_a  #=> [[1,2,3],[1,2,4],[1,3,4],[2,3,4]]
 a.combination(4).to_a  #=> [[1,2,3,4]]
 a.combination(0).to_a  #=> [[]] # one combination of length 0
 a.combination(5).to_a  #=> []   # no combinations of length 5
 ```
 
*  **#concat(other_ary)**  
   Takes in an array as an argument and combines it with the array the method was invoked on. 

 ```
 [ "a", "b" ].concat( ["c", "d"] ) #=> [ "a", "b", "c", "d" ]
 
 a = [ 1, 2, 3 ]
 a.concat( [ 4, 5 ] )
 a     #=> [ 1, 2, 3, 4, 5 ]
 ```
 
*  **#cycle(n=nil)**
   Can be called with a block or without a block. When called with a block it will loop *n* times, each time executing the code inside the block. If no block is given, will return an Enumerator.  
	 
 ```
 a = ["a", "b", "c"]
 a.cycle { |x| puts x }     # print, a, b, c, a, b, c,.. forever.
 a.cycle(2) { |x| puts x }  # print, a, b, c, a, b, c.
 ```
 
*  **#drop(n)**
   Drops the first *n* elements in the given array, and returns a new array without those elements. 
	 
	```
  a = [1, 2, 3, 4, 5, 0]
  a.drop(3)  #=> [4, 5, 0]
	```
* 	**#drop_while**
    When called with a block, the method will drop the elements for which the block returns true. The array returned contains the remaining elements from the original array. 
		
  ```
  a = [1, 2, 3, 4, 5, 0]
  a.drop_while {|i| i < 3 }   #=> [3, 4, 5, 0]
  ```

* **#initialize_copy(ary)/#replace(ary)**
  Takes in an array as an argument, and replaces the array it was invoked on with the new array.  
	
 ```
 a = [ "a", "b", "c", "d", "e" ]
 a.replace([ "x", "y", "z" ])   #=> ["x", "y", "z"]
 a    #=> ["x", "y", "z"]
```
		
* 	**#rotate(n =1)**
   Rotates the order of the elements in an array, so that the first element will be the element in position *n* .
	 The default position is 1, and when called with a negative number, the count will start from the end of the array. 
	 
  ```
 a = [ "a", "b", "c", "d" ]
 a.rotate         #=> ["b", "c", "d", "a"]
 a   #=> ["a", "b", "c", "d"]
 a.rotate(2)      #=> ["c", "d", "a", "b"]
 a.rotate(-3)     #=> ["b", "c", "d", "a"] 
 ```
	
	This is it.. I bet there are more hidden methods out there, but I guess this is enough for now... 
	I'm not sure when I'll use them, but it's good to know they're here ;)
	
