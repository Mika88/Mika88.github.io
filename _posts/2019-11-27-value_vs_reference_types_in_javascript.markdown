---
layout: post
title:      "Value Vs. Reference Types in JavaScript"
date:       2019-11-27 18:17:24 +0000
permalink:  value_vs_reference_types_in_javascript
---

JavaScript has two categories of data types: **Value types**, also known as **primitive types**, and **reference types**.

> In computer science and computer programming, a data type or simply type is an attribute of data which tells the compiler or interpreter how the programmer intends to use the data. - *Wikipedia*

**Primitive Types**

*ES6 has 6 different primitive types:*

1. *String* -- 'Hello World'
2. *Number* -- 32, 1.5
3. *Boolean* -- true/false
4. *null*
5. *undefined*
6. *Symbol*

When we assign a primitive type value to a variable the actual value is stored in that variable in memory. 

```
let x = 5;
let y = x;

x = 10;

```
Above we declared two variables `x` and `y`.  
`x` was assigned to a number, so now it contains a primitive type value, and `y` was assigned to `x`, and then we reassigned `x` to a different value. 

If we log both `x` and `y` now, what should the output be?

```
console.log(x, y); // -> 10, 5
```
*Why is that?*

The reason we get this output is because `x` and `y` are two different variables, they are stored in two different places in memory and are independent of each other.
Since `x` is a primitive, it contains the value that was assigned to it --> `5`,
and when we assign `x` to `y`, we actually copying the value of `x` to `y`, so now `y` contains `5`.
Now, when `x` gets reassigned the value of `10`, it does not affect `y`, which is still `5`.

**Reference Types**

*ES6 has 3 reference types:*

1. *Object*
2. *Array*
3. *Function*

--> Arrays and functions are actually objects, so we can say that JavaScript has one reference type which is an *Object*.

Unlike with primitive types, when we assign a variable a reference type value, the value itself is not stored inside the variable. As the name suggests, with reference type values, a reference to the value is what stored in the variable. 

```
let person = {
  name: 'Jack',
	age: 35
}

let user = person

person.age = 40

```

In this example, we created an object and assigned it to the `person` variable. `person` has two properties, `name` and `age`.  The object itself is not stores in `person`, instead, the address to the object in memory is what gets stored inside the `person` variable. 
Also, we declared a new variable and assigned it `person` and then changed the age property of `person`.
Now, if we to log out the `user` variable, what would happen?
 
```
console.log(user); // -> { name: 'Jack', age: 40 } 
```
Over here, we can see that the `age` property was changed. 

*Why is that?*

**variable** --> **Address**

`person` -->  <#100>

`user` -->  <#100>

When we assigned `person` an object, we set it to the address of that object (<#100>) , and not the object itself which is stored in a different place. 
When we set `person` to `user`, again, the address that is stored in `person` is what got assigned.
Both `person` and `user` are pointing to the same object in memory, this is why when we change the actual object, it will be reflected in both `person` and `user`. 
    

