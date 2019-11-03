---
layout: post
title:      "Java Under The Hood"
date:       2019-11-03 23:49:29 +0000
permalink:  java_under_the_hood
---


Java is a compiled and interpreted language, which means that in order to execute a Java program, the code needs to first be compiled and then it gets executed at runtime.  

**The Compilation Phase**

Let's say we have a simple Java program that prints out "Hello World": 

```
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

For my program I'm using IntelliJ as a Java code editor. The program is stored in a `Main.java` file. If we execute it in IntelliJ, it will run the `javac Main.java` command under the hood, which invokes the compiler. The compiler comes with a package that's called the Java Development Kit (JDK) that we need to download to our local environment.
During the compilation phase, the compiler translates the source code above into a Java byte code, a code format that computers can read. The byte code gets stored in a file with `class` extension, in our example, `Main.class`.

**The Execution Phase**

For the execution phase we need a Java Runtime Environment (JRE). 
A JRE is a software that contains the Java class libraries, the Java class loader and the Java Virtual Machine. 
Basically it's the environment in which Java programs are able to execute. 
Any platform that has JRE can run Java byte code, which makes Java a platform independent language. 

As previously mentioned, the JRE contains the Java Virtual Machine (JVM). During execution, the JVM translates the byte code into the native code of the computer’s operating system, like Windows, Mac orLinux, which enables the program to run on your computer. 


**To Recap**

To set up a Java program we need 3 main things:

1. Java Development Kit (JDK) 
2. Java Virtual Machine (JVM)
3. Java Runtime Environment (JRE) 

Each component has an important role in the compilation and execution of a Java program.

During compilation : *Source Code --> Java Compiler --> Java Byte Code *

During execution: *Byte Code --> Java Virtual Machine --> Native Code*
