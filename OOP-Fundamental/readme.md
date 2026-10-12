# Week 3: Object-Oriented Programming (OOP) Fundamentals

This chapter introduces Java's object-oriented programming concepts: classes, objects, fields, constructors, and methods. Examples compare Java with Python to help you understand the differences.

## 3.1 Java Methods (Functions): The Building Blocks

In Python, you can define standalone functions using `def`. In Java, methods must be declared inside a class.

* **Value-returning methods:** Specify a return type, such as `int` or `String`, and use `return` to send a value back.
* **`void` methods:** Perform an action without returning a value.

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public void displayMessage() {
        System.out.println("Hello, Java!");
    }
}
```

**Python vs. Java**

| Python                              | Java                           |
| ----------------------------------- | ------------------------------ |
| `def add(a, b):`                    | `public int add(int a, int b)` |
| `return a + b`                      | `return a + b;`                |
| No explicit return type required    | Return type must be declared   |
| Functions can exist outside classes | Methods belong to classes      |

**Key idea:** Java methods define behavior inside classes. Next, we will see how classes organize both data and behavior.

## 3.2 Procedural vs. Object-Oriented Programming

| Aspect         | Procedural Programming                          | Object-Oriented Programming (OOP)                                                                      |
| -------------- | ----------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Focus**      | Functions, e.g., `printStudentInfo(name, gpa)`  | Objects, e.g., `student1.displayProfile()`                                                             |
| **Data**       | Variables, e.g., `String name = "Alex";`        | Object fields, e.g., `student1.name`                                                                   |
| **Code reuse** | Call the same function with different arguments | Create multiple objects from one class, e.g., `new Student("Alex", 3.8)` and `new Student("Sam", 3.2)` |


For example, a procedural program might use a function named `printStudentInfo()`. An object-oriented program can organize a student's name, ID, GPA, and related methods in a `Student` class.

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

These fields belong to each `Student` object.

## 3.5 Constructors

A **constructor** initializes an object when it is created.

Rules:

* The constructor name must match the class name.
* A constructor has no return type, not even `void`.
* Java provides a default no-argument constructor only if no constructor is declared.

```java
public class Student {
    String name;
    int studentId;

    public Student(String name, int studentId) {
        this.name = name;
        this.studentId = studentId;
    }

    public Student() {
        this.name = "Unknown";
        this.studentId = 0;
    }
}
```

The class has two constructors:

* `Student(String name, int studentId)` initializes the fields using supplied values.
* `Student()` initializes the fields with `"Unknown"` and `0`.

This is called **constructor overloading**: defining multiple constructors with different parameter lists.

## 3.6 The `this` Keyword

The `this` keyword refers to the current object. It is especially useful when a parameter has the same name as an instance field.

```java
public Student(String name, int studentId) {
    this.name = name;
    this.studentId = studentId;
}
```

* `this.name` refers to the object's field.
* `name` refers to the constructor parameter.

Without `this`, the distinction between the field and parameter would be less clear.

## 3.7 Instance Methods

**Instance methods** define what an object can do. They can access the object's instance fields.

```java
public class Student {
    String name;
    double gpa;

    public Student(String name, double gpa) {
        this.name = name;
        this.gpa = gpa;
    }

    public boolean isHonorRoll() {
        return gpa >= 3.5;
    }

    public void displayProfile() {
        System.out.println("Name: " + name);
        System.out.println("GPA: " + gpa);
        System.out.println("Honor Roll: " + isHonorRoll());
    }
}
```

In this example:

* `isHonorRoll()` returns `true` if the GPA is at least 3.5; otherwise, it returns `false`.
* `displayProfile()` prints the student's information and returns no value (`void`).
* Both methods access fields belonging to the current object.

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

**Remember:** Java requires you to declare parameter types and a return type.

## 3.8 Creating and Using Objects

Use `new` to create an object. Use the dot operator (`.`) to access its fields and call its methods.

```java
public class Main {
    public static void main(String[] args) {
        Student student1 = new Student("Alex", 3.85);

        student1.displayProfile();
    }
}
```

**Output:**

```text
Name: Alex
GPA: 3.85
Honor Roll: true
```

The expression `new Student("Alex", 3.85)` creates a `Student` object and calls its constructor.

The variable `student1` holds a reference to that object.

## 3.9 Primitive Variables vs. Object References

Java variables can hold primitive values or references to objects.

| Feature  | Primitive                  | Object Reference              |
| -------- | -------------------------- | ----------------------------- |
| Examples | `int`, `double`, `boolean` | `Student`, `String`, arrays   |
| Stores   | A primitive value          | A reference to an object      |
| Example  | `int a = 5;`               | `Student s1 = new Student();` |

Consider the following code:

```java
Student s1 = new Student("Alex", 3.85);
Student s2 = s1;

s2.name = "Jordan";

System.out.println(s1.name);
```

**Output:**

```text
Jordan
```

Both `s1` and `s2` refer to the **same object**. Assigning `s1` to `s2` copies the reference, not the object.

Therefore, changing the object's name through `s2` also affects what you see through `s1`.

## 3.10 Complete Example: Student Class

The following example combines fields, a constructor, methods, and object creation.

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

class Main {
    public static void main(String[] args) {
        Student student1 = new Student("Alex", 1001, 3.85);
        Student student2 = new Student("Sam", 1002, 3.20);

        student1.displayProfile();
        System.out.println();

        student2.displayProfile();
    }
}
```

**Output:**

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

Notice that both objects use the same class but store different data.

## Summary

* **Class:** A blueprint for objects.
* **Object:** An instance of a class.
* **Fields:** Store an object's state.
* **Constructor:** Initializes an object.
* **`this`:** Refers to the current object.
* **Methods:** Define behavior and may return a value or use `void`.
* **`new`:** Creates an object.
* **Dot operator (`.`):** Accesses members through an object reference.
* **Object references:** Multiple variables can refer to the same object.

**The big idea:** OOP combines data (fields) and behavior (methods) into objects, making programs easier to organize, reuse, and maintain.
