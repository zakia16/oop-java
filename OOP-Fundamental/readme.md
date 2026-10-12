# Week 3: Object-Oriented Programming (OOP) Fundamentals

This module introduces Java OOP concepts: classes, objects, fields, constructors, and methods.

## 3.1 Procedural vs. Object-Oriented Programming

| **Aspect**     | **Procedural Programming**              | **Object-Oriented Programming**      |
| -------------- | --------------------------------------- | ------------------------------------ |
| **Focus**      | Functions and step-by-step instructions | Objects containing data and behavior |
| **Data**       | Variables and data structures           | Fields inside objects                |
| **Code Reuse** | Functions and modules                   | Classes and objects                  |

## 3.2 Classes and Objects

* **Class:** A blueprint defining an object's fields and methods.
* **Object:** An instance of a class, created using `new`.

```text
Class: Student
----------------
name: String
studentId: int
gpa: double
       |
       v
Object: student1
----------------
name = "Alex"
studentId = 1001
gpa = 3.85
```

## 3.3 Defining a Class and Instance Variables

**Instance variables** (fields) store an object's data. Each object has its own instance variables.

```java
public class Student {
    String name;
    int studentId;
    double gpa;
}
```

## 3.4 Constructors

A **constructor** initializes an object when it is created.

* Has the same name as the class.
* Has no return type, not even `void`.
* Java provides a default no-argument constructor only when no constructor is declared.

```java
public class Student {
    String name;
    int studentId;

    public Student(String name, int studentId) {
        this.name = name;
        this.studentId = studentId;
    }

    public Student() {
        name = "Unknown";
        studentId = 0;
    }
}
```

## 3.5 The `this` Keyword

`this` refers to the current object. It distinguishes instance variables from parameters with the same name.

```java
public Student(String name) {
    this.name = name;
}
```

Here, `this.name` refers to the field, while `name` refers to the parameter.

## 3.6 Instance Methods

**Instance methods** define what an object can do. They can access and modify its fields.

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

* `isHonorRoll()` returns a `boolean`.
* `displayProfile()` prints information and returns nothing (`void`).

## 3.7 Creating and Using Objects

Use `new` to create objects and the dot operator (`.`) to call their methods.

```java
public class Main {
    public static void main(String[] args) {
        Student student1 = new Student("Alex", 101);

        student1.displayProfile();
    }
}
```

## 3.8 Primitives vs. Objects

| **Feature**         | **Primitive**              | **Object**                      |
| ------------------- | -------------------------- | ------------------------------- |
| **Examples**        | `int`, `double`, `boolean` | `Student`, `String`, arrays     |
| **Variable stores** | The value                  | A reference to the object       |
| **Object data**     | Not applicable             | Typically stored in heap memory |

```java
int a = 5;
Student s1 = new Student("Alex", 101);
Student s2 = s1;
```

Here, `s1` and `s2` refer to the **same object**. Changing the object's fields through either reference affects that same object.

**Summary:** Classes define objects, constructors initialize them, fields store their state, and methods define their behavior.
