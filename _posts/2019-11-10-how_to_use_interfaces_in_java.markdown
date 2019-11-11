---
layout: post
title:      "How to use interfaces in Java"
date:       2019-11-11 00:50:05 +0000
permalink:  how_to_use_interfaces_in_java
---


**The Problem** 

When classes are directly dependent on each other, a change in one class can affect the other class, or classes. This is not optimal as it can cause code breaks or the need to change related code in many different places. 

**This is where interfaces come in
**

Interfaces are used to minimize the impact of one class on the other.
They mainly specify a behavior, a concept.
Their focus is on what is done, as opposed to a class that is more about how something should be done. 

Interfaces are similar to classes in Java, they include a group of related methods, but the difference is that interfaces hold method declarations with empty bodies, for example: 

```
public interface Resizable {
    void resize();
}
```

To show where interfaces come into play let’s first look into an example of two dependant classes:

```
public class BMICalculator {
    private double height;
    private double weight;
    
    public BMICalculator(double height, double weight) {
        this.height = height;
        this.weight = weight;
    }
    
    public double calculateBMI() {
       return weight/(Math.pow(height, 2)) ;
    }
}

```


Above I've created a BMICalculator class with `height` and `weight` fields and  a `calculateBMI` method.
I've used the metric system for the BMI formula. 

Next we will create a `ClientReport` class:


```
public class ClientReport {
  private BMICalculator calculator;

  public ClientReport() { 
      calculator = new BMICalculator(165, 57);
  }

  public void show() {
      var bmi = calculator.calculateBMI();
      System.out.println(bmi);
  }
}
```

As shown in the code above, in order to show the client's BMI, we need to instantiate an instance of the `BMICalculator` class, and then use it in the `show` method to print it on the screen. 
This is a clear example of closely dependant classes. 
If let's say we decide to change the BMI formula from implementing the metric system to the Imperial system, we would need to refactor the code both in the `BMICalculator` class, and the `ClientReport` class. 

**Creating an Interface**

In our example it makes sense to create an interface that will be resposible of the behavior of the `BMICalculator`, so in case we decide to change its implementation the `ClientReport` class won't be affected.

First let's change the name of the `BMICalculator` class to `MetricBMICalculator` to specify the type of calculator:

```
public class MetricBMICalculator {
    private double height;
    private double weight;

    public MetricBMICalculator(double height, double weight) {
        this.height = height;
        this.weight = weight;
    }

    public double calculateBMI() {
       return weight/(Math.pow(height, 2));
    }
}

```

Next we need to create the `BMICalculator` interface:

```
public interface BMICalculator {
    double calculateBMI();
}

```

We can see here that the `calculateBMI` is only being declared, with no implementation. Also, we don't need the `public` access modifier since all methods in an interface are public by default. 
In order for the `MetricBMICalculator` to use the `BMICalculator` interface we need to add the `implements` keyword, like so: 

```
public class MetricBMICalculator implements BMICalculator {
    private double height;
    private double weight;

    public MetricBMICalculator(double height, double weight) {
        this.height = height;
        this.weight = weight;
    }

    @Override
    public double calculateBMI() {
       return weight/(Math.pow(height, 2));
    }
}

```

Over here we use the `@Override` annotation because we are overriding the `calculateBMI()` method from the `BMICalculator` interface. Using this annotation signals Java that we are overriding a method which helps to prevent errors.  

Now it's time to refactor the code in the `ClientReport` class to use the `BMICalculator` interface and not the `MetricBMICalculator` class: 

```
public class ClientReport {
  private BMICalculator calculator;

  public ClientReport(BMICalculator calculator) {
      this.calculator = calculator;
  }

  public void show() {
      var bmi = calculator.calculateBMI();
      System.out.println(bmi);
  }
}

```

As you can see, we are no longer instantiating a `MetricBMICalculator` instance inside of a `ClientReport` class, which is what we wanted, because this is not its responsibility. We want these two classes to be as less dependable as possible. 

**It All Comes Together..**

It is the responsibility of the `Main` class to instantiate and implement objects, so in our example the `Main` class should look like this:

```
public class Main {
    public static void main(String[] args) {
        var calculator = new MetricBMICalculator(160, 58);
        var report = new ClientReport(calculator);
    }
}
```

In this specific case we used a `MetricBMICalculator` object, and passed it to the `ClientReport` object. If suddenly we decide to use a different calculator, the `ClientReport` object will not be affected. 



