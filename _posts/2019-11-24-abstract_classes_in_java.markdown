---
layout: post
title:      "Abstract Classes in Java"
date:       2019-11-24 22:38:30 +0000
permalink:  abstract_classes_in_java
---

In Java an abstract class is declared with the `abstract` keyword.
Usually an abstract class acts as a parent class to a number of subclasses that are meant to derive/inherit a common behavior from that abstract class. These subclasses can also be of an abstract type, or they can be regular classes, also known as concrete classes. 
One of the main characteristics of an abstract class is that it cannot be instantiated.
It is possible to declare methods inside an abstract class, which may or may not be implemented in an extended subclass of the abstract class. We can also declare abstract methods, which unlike regular methods, have to be implemented in all of its subclasses. 

To demonstrate how an abstract class works let's create a `Vegetable` abstract class, and let's say it has a `Broccoli`, a `Cabbage` and an `Onion` subclasses: 

```
//abstract parent class
abstract class Vegetable{
   
   //abstract method
   public abstract void sayColor();
	 
}

//Concrete Broccoli class that extends the Vegetable class
public class Broccoli extends Vegetable{

   public void sayColor(){
	   System.out.println("I am green");
    }
  
 }
 
 public class Main {

   public static void main(String args[]){
     Vegetable object = new Broccoli();
    	object.sayColor();
   }
}

```

Output:

```
I am green
```
As we can see in the example above, the `Broccoli` class extends the `Vegetable` class, which implements the `sayColor()` abstract method, declared in the `Vegetable` superclass. 

However, if we will comment out the implementation of the `sayColor()` abstract method from the `Broccoli` class, we will get an error:

```
public class Broccoli extends Vegetable{
//    public void sayColor(){
//        System.out.println("I am green");
//    }
}

```

Output:

 `Error:(3, 8) java: com.company.Broccoli is not abstract and does not override abstract method sayColor() in com.company.Vegetable`

From this example we can see that once we declare an abstract method inside an abstract class, it must be implemented in the extended subclass. 

We use abstract methods if we want all of our subclasses to inherit a certain behavior, in our example, all vegetables have colors, so they all should implement the `sayColor()` method. 
However, sometimes we might have a behavior that not all of the subclasses should inherit, and that is applicable to only some of the subclasses. 

Following our example, let's say we want to create a method that receives  the number of layers a vegetable has as an argument, and prints it out to the console. In our example, only the `Onion` and `Cabbage` classes have layers, so it would not make sense to implement this method in the `Broccoli` class.

```
abstract class Vegetable{
   
   public abstract void sayColor();
	 
	 public void layersCount(int layers) {
	    System.out.println("I have " + layers + "  layers");
	    
	 }
}

public class Onion extends Vegetable{
   public void sayColor(){
	   System.out.println("I am yellow");
   }	 
}

public class Main {

   public static void main(String[] args) {
        Vegetable object = new Onion();
        object.sayColor();
				object.layersCount(20)
    }
}

```

Output: 

```
I am yellow
I have 20 layers
```
As was mentioned before, we don't need to implement the `layersCount()` method in the `Broccoli` class, and if we run our program again, with the `Main` class looking like so:

```
public class Main {

   public static void main(String[] args) {
        Vegetable object = new Broccoli();
        object.sayColor();
    }
}
```
The output will be `I am green`, as before, with no errors, since the `layersCount()` method is not abstract. 

There is a case in which we don't have to implement an abstract method in an abstract class's subclass, and this is if we declare it as `abstract` as well. 
Going back to the `Onion` class, since there are a few types of onions, such as Green Onion, Yellow Onion or Pearl Onion, we can change the `Onion` class to also be an abstract class: 

```
abstract class Onion extends Vegetable {
//    public void sayColor(){
//        System.out.println("I am yellow");
//    }
}
```
Above the abstract method `sayColor` is commented out, and when the program is run there are no errors, because now the `Onion` class is abstract. 
 
 
