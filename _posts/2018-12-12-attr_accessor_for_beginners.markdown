---
layout: post
title:      "Attr_accessor for beginners"
date:       2018-12-12 15:10:16 -0500
permalink:  attr_accessor_for_beginners
---

Even though the idea of attr_accessor is pretty simple, it mainly sets and gets the instance variables of a certain class, something about not seeing what actually happens with the getter and setter methods made me feel a bit confused about how it works when I started with Ruby. 

As we know, in OO Ruby we use classes , and each class has certain functions which are executed by the classe's methods. 
The attr_accessor method is a built-in Ruby method that like it's name, allows us to access attributes. The method is  both resposible for setting and getting the different attributes we wish our instances to have. In other words, we can decide on a property, set it, have an access to it and if we choose to, we can also change it. 
For example,
let's say we build a Student class. 
```
class Student
  attr_accessor :name, :language
  def initialize(name, language)
	 @name = name
	 @language = language
  end
end

bob = Student.new
bob.name = "Bob"
bob.name # => "Bob"

bob.language = "Ruby"
bob.language # => "Ruby"
```
How all of this is possible with only one method, you might ask?
This is possible because attr_accessor  actually contains two methods in it: 
attr_writer and attr_reader. 

The attr_reader method gives us the ability to read the attribute, however, it won't let us assign the attribute (in this case the name and language)

```
 class Student
  attr_reader :name, :language
  def name
	 @name 
  end

 def language
  @language 
 end
end

bob = Student.new
bob.name  # => nil
bob.name # => no method error

bob.language  # => nil
bob.language # => no method error
```

In order to assign the attribute we use the attr_writer method:

```
 class Student
  attr_writer :name, :language
  def name=(value)
   @name = value
  end

 def language=(value)
  @language = value
 end
end
```


Together, the methods give us the ability to both set an attribute and access it:

```
class Student
 attr_reader :name, :language
 attr_writer :name, :language
	
  def name=(value)
   @name = value
  end

 def language=(value)
  @language = value
 end
 
 def name
  @name 
 end

 def language
  @language 
 end
end


bob = Student.new
bob.name = "Bob"
bob.name # => "Bob"

bob.language = "Ruby"
bob.language # => "Ruby"
```

The attr_writer also gives us the ability to change an attribute if we want to: 

```
bob.name = "Bobby"
bob.name # =>  "Bobby"
```

The example above is quite long though, right? 
here is where the attr_accessor is useful, it contains both attr_reader and attr_writer, allowing us to shorten our code: 

```
class Student
 attr_accessor :name, :language
 def initialize(name, language)
  @name = name
  @language = language
 end
end
```

This is a short behind the scenes explanation of the attr_accessor method.. 
I hope it helps :)



