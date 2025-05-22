---
title: "The final Keyword in Java"
seoTitle: "Java "final" Keyword Explained"
seoDescription: "Learn about the `final` keyword in Java, its usage with variables, methods, classes, and its implications in inheritance and security"
datePublished: Thu May 22 2025 12:16:04 GMT+0000 (Coordinated Universal Time)
cuid: cmazc5k3e000i09js6as3garr
slug: the-final-keyword-in-java
tags: java, final, deploying-java-based-applications-using-maven-sonarqube-jenkins-argo-cd-and-finally-deployment-on-amazon-eks, finally, final-keyword-and-const-keyword, final-keyword

---

The `final` keyword in Java is a non-access modifier that provides restrictions on classes, methods, and variables. It's one of the most important keywords for controlling inheritance, method overriding, and variable reassignment.

## 1\. `final` with Variables

When a variable is declared as `final`, it becomes a constant and cannot be reassigned after initialization.

### Instance Variables

```java
public class Student {
    private final String studentId;
    private final int rollNumber = 101; // initialized at declaration
    
    public Student(String id) {
        this.studentId = id; // must be initialized in constructor
    }
    
    // studentId cannot be changed after this point
}
```

### Local Variables

```java
public void demonstrateFinalVariables() {
    final int x = 10;
    // x = 20; // Compilation error - cannot reassign
    
    final List<String> names = new ArrayList<>();
    names.add("John"); // This is allowed - we're modifying the object
    // names = new ArrayList<>(); // This would cause compilation error
}
```

### Static Final Variables (Constants)

```java
public class Constants {
    public static final double PI = 3.14159;
    public static final String APP_NAME = "MyApplication";
    
    // Blank final static variable - must be initialized in static block
    public static final String DATABASE_URL;
    
    static {
        DATABASE_URL = "jdbc:mysql://localhost:3306/mydb";
    }
}
```

## 2\. `final` with Methods

A `final` method cannot be overridden by subclasses.

```java
class Parent {
    public final void displayInfo() {
        System.out.println("This method cannot be overridden");
    }
    
    public void regularMethod() {
        System.out.println("This can be overridden");
    }
}

class Child extends Parent {
    // This would cause compilation error
    // public void displayInfo() { } // Cannot override final method
    
    @Override
    public void regularMethod() {
        System.out.println("Overridden method");
    }
}
```

### Real-world Example

```java
public abstract class Shape {
    protected double area;
    
    // Template method pattern - algorithm shouldn't be changed
    public final double getAreaWithBorder(double borderWidth) {
        double baseArea = calculateArea();
        double borderArea = calculateBorderArea(borderWidth);
        return baseArea + borderArea;
    }
    
    // These can be overridden by subclasses
    protected abstract double calculateArea();
    protected abstract double calculateBorderArea(double borderWidth);
}
```

## 3\. `final` with Classes

A `final` class cannot be extended (subclassed).

```java
public final class ImmutablePerson {
    private final String name;
    private final int age;
    
    public ImmutablePerson(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String getName() { return name; }
    public int getAge() { return age; }
}

// This would cause compilation error
// class ExtendedPerson extends ImmutablePerson { }
```

### Famous Final Classes in Java

* `String` class
    
* All wrapper classes (`Integer`, `Double`, `Boolean`, etc.)
    
* `LocalDate`, `LocalTime`, `LocalDateTime`
    

## 4\. `final` with Parameters

Method parameters can be declared as `final` to prevent reassignment within the method.

```java
public void processData(final String data, final List<Integer> numbers) {
    // data = "new value"; // Compilation error
    // numbers = new ArrayList<>(); // Compilation error
    
    // But you can still modify the object's state
    numbers.add(42); // This is allowed
    
    System.out.println("Processing: " + data);
}
```

## 5\. Blank Final Variables

Final variables that are not initialized at the point of declaration.

```java
public class BlankFinalExample {
    private final String name; // blank final instance variable
    private static final String APP_VERSION; // blank final static variable
    
    // Instance blank final must be initialized in constructor
    public BlankFinalExample(String name) {
        this.name = name;
    }
    
    // Static blank final must be initialized in static block
    static {
        APP_VERSION = "1.0.0";
    }
}
```

## 6\. `final` and Collections

```java
public class CollectionExample {
    private final List<String> items = new ArrayList<>();
    
    public void addItem(String item) {
        items.add(item); // Allowed - modifying content
    }
    
    public void clearItems() {
        items.clear(); // Allowed - modifying content
    }
    
    // This method would cause compilation error
    // public void replaceList() {
    //     items = new ArrayList<>(); // Cannot reassign final variable
    // }
    
    public List<String> getItems() {
        return Collections.unmodifiableList(items); // Return immutable view
    }
}
```

## 7\. Performance Implications

The `final` keyword can provide performance benefits:

```java
public class PerformanceExample {
    private static final String CONSTANT = "Hello"; // JVM can optimize
    
    public final void criticalMethod() {
        // JVM can inline this method for better performance
        System.out.println("Critical operation");
    }
}
```

## Interview Questions and Answers

### Beginner Level

**Q1: What is the** `final` keyword in Java? **A:** The `final` keyword is a non-access modifier that restricts modification. It can be applied to variables (making them constants), methods (preventing overriding), and classes (preventing inheritance).

**Q2: Can you change the value of a final variable?** **A:** No, once a final variable is initialized, its reference cannot be changed. However, if it's an object reference, the object's internal state can still be modified.

**Q3: What happens if you don't initialize a final variable?** **A:** For instance variables, you must initialize them either at declaration or in the constructor. For static variables, you must initialize them at declaration or in a static block. Otherwise, you'll get a compilation error.

### Intermediate Level

**Q4: What is the difference between final, finally, and finalize?** **A:**

* `final`: A keyword for restrictions (variables, methods, classes)
    
* `finally`: A block that executes after try-catch, regardless of exceptions
    
* `finalize()`: A method called by garbage collector before object destruction (deprecated in Java 9+)
    

**Q5: Can a final method be overloaded?** **A:** Yes, final methods can be overloaded but cannot be overridden. Overloading creates new methods with different signatures, while overriding replaces the parent method implementation.

```java
class Example {
    public final void process(String data) { }
    public final void process(int number) { } // Overloading is allowed
}
```

**Q6: Why is the String class final in Java?** **A:** String is final to ensure immutability and security. If String could be extended, someone could create a malicious subclass that changes behavior, potentially compromising security in areas like file paths, URLs, or database connections.

### Advanced Level

**Q7: Explain blank final variables with an example.** **A:** Blank final variables are final variables declared without initialization. They must be initialized exactly once before use.

```java
public class BlankFinalDemo {
    private final int value; // blank final
    
    public BlankFinalDemo(int val) {
        if (val > 0) {
            this.value = val; // initialization in constructor
        } else {
            this.value = 1; // must initialize in all code paths
        }
    }
}
```

**Q8: Can you have a final abstract method or final abstract class?** **A:** No, this is contradictory. Abstract methods are meant to be overridden, while final methods cannot be overridden. Similarly, abstract classes are meant to be extended, while final classes cannot be extended.

**Q9: What is the effectively final concept in Java 8?** **A:** A variable is effectively final if it's not declared final but is never reassigned after initialization. This is important for lambda expressions and inner classes.

```java
public void demonstrateEffectivelyFinal() {
    String message = "Hello"; // effectively final
    // message = "Hi"; // if uncommented, it's no longer effectively final
    
    Runnable r = () -> System.out.println(message); // works because message is effectively final
}
```

**Q10: How does** `final` affect inheritance and polymorphism? **A:** Final classes cannot be extended, breaking inheritance chains. Final methods cannot be overridden, limiting polymorphic behavior. However, final variables don't affect inheritance directly but ensure data integrity.

### Tricky Questions

**Q11: What will be the output of this code?**

```java
class Parent {
    public final void display() {
        System.out.println("Parent display");
    }
}

class Child extends Parent {
    public void display() { // Will this compile?
        System.out.println("Child display");
    }
}
```

**A:** This code will not compile because you cannot override a final method. The compiler will throw an error.

**Q12: Is it possible to modify a final object?** **A:** Yes, you can modify the internal state of a final object reference, but you cannot reassign the reference itself.

```java
final List<String> list = new ArrayList<>();
list.add("item"); // Allowed - modifying object state
// list = new ArrayList<>(); // Not allowed - reassigning reference
```

The `final` keyword is crucial for creating immutable objects, ensuring security, enabling certain optimizations, and controlling inheritance hierarchies. Understanding its various applications will help you write more robust and secure Java code.