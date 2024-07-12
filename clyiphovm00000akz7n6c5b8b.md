---
title: ""Getting Started with Your First Java Program: A Beginner's Guide""
seoTitle: "Java Hello World Program"
seoDescription: "Introduction to Java. Hello World Java Program."
datePublished: Fri Jul 12 2024 13:00:52 GMT+0000 (Coordinated Universal Time)
cuid: clyiphovm00000akz7n6c5b8b
slug: getting-started-with-your-first-java-program-a-beginners-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720789111219/ac5237b9-39ac-412e-b425-49cc7199886c.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720789244239/ad181806-399c-42be-ad7e-b18a4eabeb75.jpeg
tags: java

---

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Explanation of the above Java Code:

1. **public class HelloWorld**:
    
    * This line declares a public class named `HelloWorld`. In Java, every application must have at least one class definition that contains the main method.
        
2. **public static void main(String\[\] args)**:
    
    * This is the main method, which is the entry point of any Java program. When you run a Java program, the JVM (Java Virtual Machine) looks for this method to start execution.
        
    * `public`: This means that the method is accessible from anywhere.
        
    * `static`: This means that the method belongs to the class, not instances of the class.
        
    * `void`: This means that the method does not return any value.
        
    * `main`: This is the name of the method. It's a special method name that the JVM looks for when running a program.
        
    * `String[] args`: This is an array of `String` objects. It allows the program to accept command-line arguments.
        
3. **System.out.println("Hello, World!");**:
    
    * This line prints the text "Hello, World!" to the console.
        
    * `System`: This is a built-in class in Java that contains useful methods and variables.
        
    * `out`: This is a static member of the `System` class, and it's an instance of `PrintStream`. It represents the standard output stream.
        
    * `println`: This is a method of the `PrintStream` class. It prints the argument passed to it (in this case, "Hello, World!") to the console and then terminates the line.
        

Try the above code in any of the free online code editors given below and execute it.  
  
1) [https://www.jdoodle.com/](https://www.jdoodle.com/)

2) [https://www.online-java.com/](https://www.online-java.com/)

3) [https://www.codechef.com/java-online-compiler](https://www.codechef.com/java-online-compiler)