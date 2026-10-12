# Week 3: Object-Oriented Programming (OOP) Fundamentals

This chapter introduces Java methods, classes, objects, fields, constructors, and object references. Examples compare Java with Python to help you understand the differences.

## 3.1 Java Methods: The Building Blocks

A **method** is a named block of code that performs a task. Methods help organize programs, reduce repeated code, and break complex problems into smaller steps.

In Python, functions are defined using `def` and can exist outside a class. In Java, methods must be declared inside a class.

### Methods That Return Values

A method can calculate a result and return it using `return`. Its return type specifies the type of value returned.

```java
public static int add(int a, int b) {
    return a + b;
}
```

Here, `int` is the return type, `add` is the method name, and `a` and `b` are parameters.

### `void` Methods

A `void` method performs an action without returning a value.

```java
public static void displayMessage() {
    System.out.println("Hello, Java!");
}
```

### Complete Example

```java
public class Calculator {
    public static int add(int a, int b) {
        return a + b;
    }

    public static void displayMessage() {
        System.out.println("Hello, Java!");
    }

    public static void main(String[] args) {
        System.out.println(add(3, 4));
        displayMessage();
    }
}
```

**Output:**

```text
7
Hello, Java!
```

The program begins executing in `main()`. The `add()` method returns `7`, while `displayMessage()` prints a message.

### Python vs. Java

| Python                                   | Java                                  |
| ---------------------------------------- | ------------------------------------- |
| `def add(a, b):`                         | `public static int add(int a, int b)` |
| No explicit return type required         | Return type must be declared          |
| Parameters do not require declared types | Parameter types must be declared      |
| Functions can exist outside classes      | Methods belong to classes             |

### Parameters and Arguments

**Parameters** are variables listed in a method definition. **Arguments** are the actual values supplied when calling the method.

```java
public static void printTwice(String message) {
    System.out.println(message);
    System.out.println(message);
}

public static void main(String[] args) {
    printTwice("Hello, Java!");
}
```

**Output:**

```text
Hello, Java!
Hello, Java!
```

Here, `message` is the parameter, and `"Hello, Java!"` is the argument.

A method can accept multiple parameters:

```java
public static void printTime(int hour, int minute) {
    System.out.println(hour + ":" + minute);
}
```

Call the method by providing arguments in the same order:

```java
printTime(11, 59);
```

**Output:**

```text
11:59
```

Do not declare types when passing arguments. Use `printTime(11, 59)`, not `printTime(int 11, int 59)`.

### Flow of Execution

Java begins execution at the first statement in `main()`. When a method is called, execution moves to that method. After the method finishes, execution returns to the statement following the call.

Methods make programs easier to read, reuse, test, and maintain.

## 3.2 Procedural vs. Object-Oriented Programming

Procedural programming organizes code around functions. Object-oriented programming (OOP) organizes data and behavior into objects.

| Aspect         | Procedural Programming                          | Object-Oriented Programming (OOP)          |
| -------------- | ----------------------------------------------- | ------------------------------------------ |
| **Focus**      | Functions, e.g., `printStudentInfo(name, gpa)`  | Objects, e.g., `student1.displayProfile()` |
| **Data**       | Variables, e.g., `String name = "Alex";`        | Object fields, e.g., `student1.name`       |
| **Code reuse** | Call the same function with different arguments | Create multiple objects from one class     |

For example, a procedural program might pass a student's name and GPA to a function. An OOP program can store the name and GPA inside a `Student` object and define methods that use that data.

**Key idea:** OOP combines data and behavior into objects.

## 3.3 Classes and Objects

A **class** is a blueprint that defines the data and behavior its objects can have.

An **object** is an instance of a class, typically created using the `new` keyword.

```text
Class (Blueprint)                 Object (Instance)
┌──────────────────────┐         ┌──────────────────────┐
│ Student              │         │ student1             │
├──────────────────────┤         ├──────────────────────┤
│ name: String         │ ------> │ name = "Alex"        │
│ studentId: int       │         │ studentId = 1001     │
│ gpa: double          │         │ gpa = 3.85           │
└──────────────────────┘         └──────────────────────┘
```

Think of a class as a blueprint for a house. The blueprint describes the structure, while each house built from it is an individual object.

## 3.4 Defining a Class and Fields

**Fields**, also called instance variables, store an object's data. Each object has its own instance fields.

```java
public class Student {
    String name;
    int studentId;
    double gpa;
}
```

Here:

* `name` stores the student's name.
* `studentId` stores the student's ID.
* `gpa` stores the student's GPA.

These fields define the data each `Student
## 3.5 Creating Objects

Use the `new` keyword to create an object.

```java
public class Main {
    public static void main(String[] args) {
        Student student1 = new Student();
        Student student2 = new Student();

        student1.name = "Alex";
        student1.studentId = 1001;
        student1.gpa = 3.85;

        student2.name = "Sam";
        student2.studentId = 1002;
        student2.gpa = 3.20;

        System.out.println(student1.name);
        System.out.println(student2.name);
    }
}
```

**Output:**

```text
Alex
Sam
```

Each object has its own fields. Changing `student1.name` does not change `student2.name`.

Because no constructor has been declared in `Student`, Java provides a default no-argument constructor.

## 3.6 Constructors

A **constructor** initializes an object when it is created. It allows you to provide initial values instead of assigning each field separately.

### Constructor Rules

* Its name must match the class name.
* It has no return type, not even `void`.
* Java provides a default no-argument constructor only if no constructor is declared.

### Example

```java
public class Student {
    String name;
    int studentId;
    double gpa;

    public Student(String name, int studentId, double gpa) {
        this.name = name;
        this.studentId = studentId;
        this.gpa = gpa;
    }
}
```

Now objects can be created with their initial values:

```java
Student student1 = new Student("Alex", 1001, 3.85);
Student student2 = new Student("Sam", 1002, 3.20);
```

The constructor initializes each student's fields during object creation.

### Constructor Overloading

A class can have multiple constructors with different parameter lists.

```java
public Student() {
    name = "Unknown";
    studentId = 0;
    gpa = 0.0;
}
```

This no-argument constructor allows you to write:

```java
Student student1 = new Student();
```

If you declare any constructor yourself, Java no longer automatically supplies the default no-argument constructor.

## 3.7 The `this` Keyword

The `this` keyword refers to the current object. It is commonly used when constructor parameters have the same names as instance fields.

```java
public Student(String name, int studentId, double gpa) {
    this.name = name;
    this.studentId = studentId;
    this.gpa = gpa;
}
```

In `this.name = name;`:

* `this.name` refers to the object's field.
* `name` refers to the constructor parameter.

This makes it clear which variable stores the object's data.

## 3.8 Instance Methods

**Instance methods** define what an object can do. Unlike the introductory `static` methods in Section 3.1, instance methods operate on a particular object and can directly access its instance fields.

Add these methods to the `Student` class:

```java
public boolean isHonorRoll() {
    return gpa >= 3.5;
}

public void displayProfile() {
    System.out.println("Name: " + name);
    System.out.println("Student ID: " + studentId);
    System.out.println("GPA: " + gpa);
    System.out.println("Honor Roll: " + isHonorRoll());
}
```

* `isHonorRoll()` returns `true` if the GPA is at least 3.5; otherwise, it returns `false`.
* `displayProfile()` prints the student's information and returns no value (`void`).

### Method Components

Consider this method:

```java
public int add(int a, int b) {
    return a + b;
}
```

| Component       | Meaning            |
| --------------- | ------------------ |
| `public`        | Access modifier    |
| `int`           | Return type        |
| `add`           | Method name        |
| `int a, int b`  | Parameters         |
| `return a + b;` | Returns the result |

## 3.9 Calling Methods Through Objects

Use the dot operator (`.`) to access an object's fields and call its instance methods.

```java
public class Main {
    public static void main(String[] args) {
        Student student1 = new Student("Alex", 1001, 3.85);

        student1.displayProfile();
    }
}
```

**Output:**

```text
Name: Alex
Student ID: 1001
GPA: 3.85
Honor Roll: true
```

The expression `student1.displayProfile()` calls the method on `student1`. The method uses that object's fields.

## 3.10 Primitive Variables vs. Object References

Java variables can store primitive values or references to objects.

| Feature      | Primitive                  | Object Reference              |
| ------------ | -------------------------- | ----------------------------- |
| **Examples** | `int`, `double`, `boolean` | `Student`, `String`, arrays   |
| **Stores**   | A primitive value          | A reference to an object      |
| **Example**  | `int a = 5;`               | `Student s1 = new Student();` |

### Example: Two References, One Object

```java
Student s1 = new Student("Alex", 1001, 3.85);
Student s2 = s1;

s2.name = "Jordan";

System.out.println(s1.name);
```

**Output:**

```text
Jordan
```

Both `s1` and `s2` refer to the same object. Assigning `s1` to `s2` copies the reference, not the object itself.

Therefore, changing the object's name through `s2` also changes the name observed through `s1`.

## 3.11 Complete Example: Student Class

The following program combines fields, constructors, `this`, instance methods, and object creation.

Save the code in a file named `Main.java`.

```java
class Student {
    String name;
    int studentId;
    double gpa;

    public Student(String name, int studentId, double gpa) {
        this.name = name;
        this.studentId = studentId;
        this.gpa = gpa;
    }

    public boolean isHonorRoll() {
        return gpa >= 3.5;
    }

    public void displayProfile() {
        System.out.println("Name: " + name);
        System.out.println("Student ID: " + studentId);
        System.out.println("GPA: " + gpa);
        System.out.println("Honor Roll: " + isHonorRoll());
    }
}

public class Main {
    public static void main(String[] args) {
        Student student1 = new Student("Alex", 1001, 3.85);
        Student student2 = new Student("Sam", 1002, 3.20);

        student1.displayProfile();
        System.out.println();

        student2.displayProfile();
    }
}
```

### Output

```text
Name: Alex
Student ID: 1001
GPA: 3.85
Honor Roll: true

Name: Sam
Student ID: 1002
GPA: 3.2
Honor Roll: false
```

### What to Notice

1. `Student` defines the fields and methods its objects have.
2. Each constructor call initializes a different object.
3. `this` distinguishes fields from parameters.
4. `displayProfile()` displays information for the object on which it is called.
5. Both students use the same class but store different data.

## Summary

* **Methods** perform tasks and may return values or use `void`.
* **Parameters** are variables declared in method definitions; **arguments** are values passed to methods.
* **Procedural programming** organizes code around functions.
* **OOP** organizes data and behavior into objects.
* **Classes** define the structure and behavior of objects.
* **Fields** store an object's state.
* **Constructors** initialize objects.
* **`this`** refers to the current object.
* **Instance methods** operate on an object's data.
* **`new`** creates an object.
* **Object references** allow multiple variables to refer to the same object.

**The big idea:** A class defines what an object has and does. An object is a specific instance with its own state.
