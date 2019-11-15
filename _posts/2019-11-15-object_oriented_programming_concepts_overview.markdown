---
layout: post
title:      "Object Oriented Programming Concepts Overview"
date:       2019-11-15 23:58:11 +0000
permalink:  object_oriented_programming_concepts_overview
---


If you have experience coding in languages such as Ruby, Java, Python, C# or JavaScript, you are probably familiar with Object Oriented Programming (OOP) patterns. 
It is a very powerful and popular style of coding, and it's important for a programmer to understand the OOP concepts,  which is why I wanted to go back to basics and make an overview of the 4 main concepts of OOP. 

Basically OOP is a paradigm that is focused on creating objects, as opposed to just functions, like in Procedural programming.  The 4 main concepts of OOP are: 

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

In this blog entry I will discuss each concept and give examples. 

**1. Encapsulation**

Encapsulation in OOP is the ability to group together related properties and methods into one unit, one object. 
Doing this allows us to keep our code organized and it prevents us from having related functions and variables scattered all over our code, which makes things confusing, messy and not very DRY. 

Let's say we want to create a flower-shop website using JavaScript. In order to calculate the price of an order we would need some variables and methods:

*The Procedural way*

```
int arrangementPrice = 50
let numberOfItems = 2
let deliveryRate = 10

function getTotalPrice(arrangementPrice, numberOfItems, deliveryRate) {
  return (arrangementPrice * numberOfItems) + deliveryRate;
}
```
*The OOP way*
```
let order = {
  arrangementPrice: 50,
  numberOfItems: 2,
  deliveryRate: 10,
	getTotalPrice: function() {
	  return (this.arrangementPrice * this.numberOfItems) + this.deliveryRate;
		}
 }
 
order.getTotalPrice();	
```
In the first example the `getTotalPrice()` function has three parameters. In contrast, in the second example these parameters are the properties of the `order` object, so by using the `this` keyword, we can reference the parameters inside `getTotalPrice()` without having to pass them as arguments. 

**2. Abstraction**

The idea behind abstraction is to hide irrelevant code, like different methods or properties of one object from other objects. 
A real life example of abstraction might be driving. In order to drive you need to know all the things that are related to the action of driving, with maybe some basic knowledge on how to start your car, how to change a tire... 
But you don't need to know exactly how the engine works, or the names of all its parts. It's not relevant for the ability to drive. All of these details are hidden from you.

The same is with objects in your code, objects need to know about just a specific part of the entire program, just what they are responsible for.

Using abstraction helps to reduce the complexity and makes code changes more secure. 
For example, in Java, we usually set the field (property)  of a class to `private`, so only that class has access to this field. This way if we decide to change the implementation of that field, we will only need to change it in one place, inside that object, and not worry that it might break the code somewhere else. 

**3. Inheritance**

The purpose of inheritance in OOP is to allow you to reuse code and to keep your code DRY. 
By allowing an object to inherit methods and properties from another object, the only thing we need to add to the child object are its specific methods and properties. For example, if we continue with our flower-shop website from before, suppose we have a user object. A user can be a customer or an admin. Customers and admins have common properties, like `username`, `email` and `password`. A customer might have a method like `createAnOrder()` that allows the customer to make a flower arrangement order. An admin might have a `createAnArrangement()` method which allows the admin to create a new arrangement instance. 

With inheritance we have a `is a` relationship between the parent object and the child object, in our example the admin object is a user. So all the properties and methods a user has access to are also accessed by the admin object.
Different languages implement inheritance in different ways. In Java, for example, we use the `extends` keyword on the child object and we mention the parent class. 

```
public class User {
  String username = "";
	String email = "";
	String password = "";
}

public class Admin extends User {
  ...
	
  public createAnOrder() {
	 ...
	}
}
	
```

**4. Polymorphism**

Polymorphism allows us to use objects differently depending on their data type. We can implement the same functions in a different way, thus preventing the usage of a lot of if statements or switch statements in our code. How does it work? 

For this example I'll use polymorphism in Ruby. 
Let's say we have an `Animal` class with a `talk` method:

```
class Animal 
  def talk(string)
	  puts string
	end
end
```
and we have several animal classes that inherit from `Animal`, like a `Cow`:

```
class Cow < Animal
  
end
```
Now, let's say we have a `Farm` class, in which we want to implement the `talk` method for different animals: 

```
class Farm
  animals = [Cow.new, Sheep.new, Dog.new]
	animals.each do |animal| 
	   if animal.instance_of?(Cow)
		   animal.talk("Mooooo")
		 elsif animal.instance_of?(Dog)
		   animal.talk("woof woof")
			  ...
				
		 end
	end
end
```
 As you can see, if we want our animals to talk, we need to create a long `if` statement..
 This is where polymorphism steps in: 
 
```
class Animal
  def talk
	end
end
```
First we just declare a talk method with no body. 
Then, we override this method in each subclass, for example:

```
class Cow < Animal
   def talk
	   puts "Moooo"
	 end
end
```
Then in our `Farm` class:

```
class Farm
  animals = [Cow.new, Sheep.new, Dog.new]
  	animals.each {|animal| animal.talk}
	end
end
```
That's it.. each animal executes a different implementation of the `talk` method because it's overridden in each subclass of `Animal`.

So there you go, the 4 concepts of OOP. I've used different languages to demonstrate that OOP is not restricted to a specific language, it is a style of coding, a paradigm, and can be used in different languages. 
