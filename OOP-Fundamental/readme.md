# Week 3: Object-Oriented Programming (OOP) Fundamentals

This chapter introduces Java methods, classes, objects, fields, constructors, and object references. Examples compare Java with Python to help you understand the differences.

## 3.1 Java Methods: The Building Blocks

A **method** is a named block of code that performs a task. Methods help organize programs, reduce repeated code, and break complex problems into smaller steps.

In Python, functions are defined using `def` and can exist **outside a class**. In Java, methods must be declared **inside a class**.

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
    System.out.println(message); // Print the message the first time
    System.out.println(message); // Print the message the second time
}

public static void main(String[] args) {
    // Call the method, passing "Hello, Java!" as the argument
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
public static void printTwice(String message, String extraText) {
    System.out.println(message + extraText); // Print the combined message the first time
    System.out.println(message + extraText); // Print the combined message the second time
}

public static void main(String[] args) {
    // Call the method, passing two string arguments
    printTwice("Hello Java", "!");
}
```

**Output:**

```text
Hello, Java!
Hello, Java!
```

Do not declare types when passing arguments. Use `printTime(11, 59)`, not `printTime(int 11, int 59)`.

### Advantages of Functions

Functions make programs easier to read, reuse, test, and maintain, as we learned in CS I when studying Python.

<img width="1215" height="696" alt="image" src="https://github.com/user-attachments/assets/c3530a5c-c622-4085-bf70-fe1e7e2ed021" />

This works well for small programs, but as programs grow, managing data and functions becomes more difficult.

### Problems with Global Data

Procedural programming uses two types of data:

- **Local data:** Declared inside a function and accessible only within that function.
- **Global data:** Declared outside functions and accessible by multiple functions.

When several functions need the same information, we often use global variables.

**What's the problem?**    
Any function can potentially modify global data, making it harder to track changes, find errors, and maintain large programs.

### Modeling the Real World

Think about real-world objects, such as people and cars. Every object has:

- **Attributes (Data):** Characteristics, such as a person's eye color or a car's horsepower.
- **Behaviors (Functions):** Actions, such as a person walking or a car braking.

It makes sense to organize related data and behaviors together.

### 3.2 The Object-Oriented Approach

**Object-Oriented Programming (OOP)** combines data and the functions that operate on that data into a single unit called an **object**.

OOP introduces four fundamental features that help organize and manage complex programs:
1. **Encapsulation**
2. **Inheritance**
3. **Polymorphism**
4. **Abstraction**

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

## 3.4 Declaring Classes

A **class declaration** defines a class and specifies its structure. In Java, a class is declared using the `class` keyword, followed by the class name and a pair of curly braces.

```java
public class MyClass {
    // Fields
    // Constructors
    // Methods
}
```
<img width="1602" height="982" alt="image" src="https://github.com/user-attachments/assets/954032b6-9580-40c1-b2ad-aeac4b0877e1" />

The **class body** (the code between the curly braces `{ }`) contains the members that define the class:


## Fields

 Fields store the data each object holds.

```java
public class Student {
    // Instance fields (attributes)
    String name;         // `name` stores the student's name.
    int studentId;      // `studentId` stores the student's ID.
    double gpa;        // `gpa` stores the student's GPA.
}
```


## Methods

**Instance methods** define what an object can do. Instance methods operate on a specific object and can directly use its fields.

Add these methods to the `Student` class:

```java
public class Student {
    String name;
    int studentId;
    double gpa;

    // Instance methods (behavior)
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
```

* `isHonorRoll()` returns `true` if the GPA is at least 3.5; otherwise, it returns `false`.
* `displayProfile()` prints the student's information and returns no value (`void`).

### Method Anatomy

<img width="1200" height="800" alt="image" src="https://github.com/user-attachments/assets/37894cdc-5e68-4128-bf70-f46a6c7cd2ef" />



## 3.5 Creating Objects & Calling Methods

Now that the Student blueprint has both fields and methods, use the **new** keyword to create objects and the **dot operator (.)** to access their data and methods.

```java
public class Main {
    public static void main(String[] args) {
        // Create two separate Student objects
        Student student1 = new Student();
        Student student2 = new Student();

        // Assign data to student1's fields
        student1.name = "Alex";
        student1.studentId = 1001;
        student1.gpa = 3.85;

        // Assign data to student2's fields independently
        student2.name = "Sam";
        student2.studentId = 1002;
        student2.gpa = 3.20;

        // Print out names to show they maintain independent values
        System.out.println(student1.name); // Prints Alex
        System.out.println(student2.name); // Prints Sam
    }
}
```

**Output:**

```text
Alex
Sam
```
**Note:**
Each object has its own fields. Changing `student1.name` does not change `student2.name`.  
**Assigning fields one by one works, but it is repetitive and easy to forget a field. Constructors solve this problem.**

[▶ Visualize this Java code step-by-step in Python Tutor](https://pythontutor.com/visualize.html#code=public%20class%20MainClass%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20//%20Create%20two%20separate%20Student%20objects%0A%20%20%20%20%20%20%20%20Student%20student1%20%3D%20new%20Student%28%29%3B%0A%20%20%20%20%20%20%20%20Student%20student2%20%3D%20new%20Student%28%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20//%20Assign%20data%20to%20student1's%20fields%0A%20%20%20%20%20%20%20%20student1.name%20%3D%20%22Alex%22%3B%0A%20%20%20%20%20%20%20%20student1.studentId%20%3D%201001%3B%0A%20%20%20%20%20%20%20%20student1.gpa%20%3D%203.85%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20//%20Assign%20data%20to%20student2's%20fields%20independently%0A%20%20%20%20%20%20%20%20student2.name%20%3D%20%22Sam%22%3B%0A%20%20%20%20%20%20%20%20student2.studentId%20%3D%201002%3B%0A%20%20%20%20%20%20%20%20student2.gpa%20%3D%203.20%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20//%20Print%20out%20names%20to%20show%20they%20maintain%20independent%20values%0A%20%20%20%20%20%20%20%20System.out.println%28student1.name%29%3B%20//%20Prints%20Alex%0A%20%20%20%20%20%20%20%20System.out.println%28student2.name%29%3B%20//%20Prints%20Sam%0A%20%20%20%20%7D%0A%7D%0A%0Aclass%20Student%20%7B%0A%20%20%20%20String%20name%3B%0A%20%20%20%20int%20studentId%3B%0A%20%20%20%20double%20gpa%3B%0A%20%20%20%20%0A%20%20%20%20public%20boolean%20isHonorRoll%28%29%20%7B%0A%20%20%20%20%20%20%20%20return%20gpa%20%3E%3D%203.5%3B%0A%20%20%20%20%7D%0A%20%20%20%20%0A%20%20%20%20public%20void%20displayProfile%28%29%20%7B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Name%3A%20%22%20%2B%20name%29%3B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Student%20ID%3A%20%22%20%2B%20studentId%29%3B%0A%20%20%20%20%20%20%20%20System.out.println%28%22GPA%3A%20%22%20%2B%20gpa%29%3B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Honor%20Roll%3A%20%22%20%2B%20isHonorRoll%28%29%29%3B%0A%20%20%20%20%7D%0A%7D&curInstr=0&mode=display&origin=opt-frontend.js&py=java)


## 3.6 Constructors

Imagine you are building a student management system. Every time a new student joins the university, you need to create a `Student` object and assign values to its fields.

```java
// for one student 3 lines of code 
student.name = "Alex";
student.studentId = 1001;
student.gpa = 3.85;
```

Imagine doing this for 100 students! That's a lot of extra code: 100 * 3 = 300 lines.

Wouldn't it be easier if we could create the object and initialize all its fields in one step?

**That's exactly what constructors are for!**

A **constructor** is a special block of code that runs automatically when `new` is called. It lets you initialize an object's fields in a single line.

### Constructor Rules
* Its name must match the class name.
* It has no return type, not even `void`.
* Java provides a default no-argument constructor only if no constructor is declared.


### 3.6.1. Default (No-Argument) Constructor
A no-argument constructor does not take any parameters. If you do not write any constructor yourself, Java invisibly provides one that sets fields to default values. 
For example:

```java
public class Student {
    String name;
    int studentId;
    double gpa;
    boolean enrolled;
}
```

You can create an object without writing a constructor:

```java
Student student1 = new Student();
```

Java initializes instance fields to their default values:

| Data Type | Default Value |
|---|---|
| `int` | `0` |
| `double` | `0.0` |
| `boolean` | `false` |
| `String` | `null` |
| Other object references | `null` |

**Note:** You can also write your own no-argument constructor to assign custom initial values. Let's see the next example:

```java
public class Student {
    String name;
    int studentId;
    double gpa;

    // Explicit no-argument constructor for default values
    public Student() {
        name = "Unknown";
        studentId = 0;
        gpa = 0.0;
    }
}

// Creating an object using the no-argument constructor:
Student student1 = new Student();
```

### 3.6.2. Parameterized Constructor
A parameterized constructor takes one or more parameters, allowing you to pass initial values during object creation.

```java
public class Student {
    String name;
    int studentId;
    double gpa;

    // Parameterized constructor used to initialize fields during object creation
    public Student(String name, int studentId, double gpa) {
        this.name = name;
        this.studentId = studentId;
        this.gpa = gpa;
    }
}

// Creating objects using the parameterized constructor:
Student student1 = new Student("Alex", 1001, 3.85);
Student student2 = new Student("Sam", 1002, 3.20);
```


### 3.6.3. Constructor Overloading

Imagine you are building a student registration system. Not every student has the same information available when they are registered.

- Sometimes, we don't know anything about the student yet.
- Sometimes, we know the student's name and ID, but their GPA is not available.
- Sometimes, we have all the information, including the GPA.

Do we need to create a different class for each situation? No!   
Java allows a class to have **multiple constructors with different parameter lists**. This is called **constructor overloading**.

Let's update our `Student` class:


```java
public class Student {
    String name;
    int studentId;
    double gpa;

    // Constructor 1: No-argument constructor
    public Student() {
        this.name = "Unknown";
        this.studentId = 0;
        this.gpa = 0.0;
    }

    // Constructor 2: Two parameters (for new students without a GPA yet)
    public Student(String name, int studentId) {
        this.name = name;
        this.studentId = studentId;
        this.gpa = 0.0;
    }

    // Constructor 3: All three parameters
    public Student(String name, int studentId, double gpa) {
        this.name = name;
        this.studentId = studentId;
        this.gpa = gpa;
    }
}

// Java picks the matching constructor based on the arguments passed:
Student student1 = new Student();                   // Calls Constructor 1
Student student2 = new Student("Jordan", 1003);     // Calls Constructor 2
Student student3 = new Student("Alex", 1001, 3.85); // Calls Constructor 3
```

**How does Java know which constructor to call?**   
Java automatically selects the matching constructor based on the number and types of arguments passed.


## 3.7 The `this` Keyword

The `this` keyword refers to the current object. It is commonly used when constructor parameters have the same names as instance fields.

```java
public class Student {
    String name;
    int studentId;
    double gpa;

    // Using 'this' to distinguish fields from parameters
    public Student(String name, int studentId, double gpa) {
        this.name = name;
        this.studentId = studentId;
        this.gpa = gpa;
    }
}
```

In `this.name = name;`:

- `this.name` refers to the object's instance field.
- `name` refers to the constructor parameter.

This makes it clear which variable stores the object's data.

Now that we understand how `this` refers to the current object, let's look at how Java variables store primitive values and refer to objects.


## 3.8 Primitive Variables vs. Object References
Primitive variables hold values directly, while object reference variables hold a reference (address) to an object in memory. Both examples below use object references, showing what happens when you **reassign a reference** versus **mutate a field on a shared object**.

### Example 1: Reassigning a Reference (String)
Consider what happens when we copy a String reference and then reassign one of the variables:

```java
String s1 = "Alex";
String s2 = s1;

s2 = "Jordan";

System.out.println(s1);
```

**Output:**
```text
Alex
```

**Why?**

Assigning one reference variable to another copies the reference. Reassigning one variable does not change what the other variable refers to.

[▶ Visualize this Java code step-by-step in Python Tutor](https://pythontutor.com/visualize.html#code=public%20class%20MainClass%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20String%20s1%20%3D%20%22Alex%22%3B%0A%20%20%20%20%20%20%20%20String%20s2%20%3D%20s1%3B%0A%0A%20%20%20%20%20%20%20%20s2%20%3D%20%22Jordan%22%3B%0A%0A%20%20%20%20%20%20%20%20System.out.println%28s1%29%3B%0A%20%20%20%20%7D%0A%7D&curInstr=0&mode=display&origin=opt-frontend.js&py=java)


### Example 2: Two References, One Shared Object (Student)

Now compare that with mutating a field inside an object when two reference variables point to the same Student instance:

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

**Why?**

Both variables refer to the same object. Changing the object's fields through one reference is visible through the other reference.

       Stack (Local Variables)                 Heap (Objects)
      +----------------------+             +---------------------------+
      |                      |             |                           |
      |  s1  ----------------|------------>|        Student            |
      |                      |             |  +---------------------+  |
      |  s2  ----------------|-------------|->| name: "Alex"        |  |
      |                      |             |  | studentId: 1001    |  |
      +----------------------+             |  | gpa: 3.85          |  |
                                           |  +---------------------+  |
                                           +---------------------------+

[▶ Visualize this Java code step-by-step in Python Tutor](https://pythontutor.com/visualize.html#code=public%20class%20MainClass%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20Student%20s1%20%3D%20new%20Student%28%22Alex%22,%201001,%203.85%29%3B%0A%20%20%20%20%20%20%20%20Student%20s2%20%3D%20s1%3B%0A%0A%20%20%20%20%20%20%20%20s2.name%20%3D%20%22Jordan%22%3B%0A%0A%20%20%20%20%20%20%20%20System.out.println%28s1.name%29%3B%0A%20%20%20%20%7D%0A%7D%0A%0Aclass%20Student%20%7B%0A%20%20%20%20String%20name%3B%0A%20%20%20%20int%20studentId%3B%0A%20%20%20%20double%20gpa%3B%0A%0A%20%20%20%20public%20Student%28String%20name,%20int%20studentId,%20double%20gpa%29%20%7B%0A%20%20%20%20%20%20%20%20this.name%20%3D%20name%3B%0A%20%20%20%20%20%20%20%20this.studentId%20%3D%20studentId%3B%0A%20%20%20%20%20%20%20%20this.gpa%20%3D%20gpa%3B%0A%20%20%20%20%7D%0A%7D&curInstr=0&mode=display&origin=opt-frontend.js&py=java)

Understanding how Java variables store values and refer to objects helps prevent accidental shared-state bugs when passing or copying references.   
Another important part of writing maintainable Java code is following consistent naming conventions.
 
## 3.9 Java Naming Conventions

Java follows standard naming conventions to make code readable, consistent, and easier to maintain.

| **Name** | **Convention** | **Examples** |
|---|---|---|
| **Class name** | Start with an uppercase letter. Use a noun. | `String`, `Color`, `Button`, `System` |
| **Interface name** | Start with an uppercase letter. Often use an adjective. | `Runnable`, `Remote`, `ActionListener` |
| **Method name** | Start with a lowercase letter. Use a verb. | `actionPerformed()`, `main()`, `print()`, `println()` |
| **Variable name** | Start with a lowercase letter. Use descriptive names. | `firstName`, `orderNumber` |
| **Package name** | Use lowercase letters. | `java.lang`, `java.util`, `java.sql` |
| **Constant name** | Use uppercase letters. Separate words with underscores (`_`). | `RED`, `YELLOW`, `MAX_PRIORITY` |


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



### Review Questions

**1. How is OOP different from procedural programming?**

<details>
<summary>Show Answer</summary>

OOP focuses on objects that bundle data and behavior together, whereas procedural programming focuses on step-by-step instructions and functions.

</details>

**2. What are the main benefits of OOP?**

<details>
<summary>Show Answer</summary>

Code reusability, modularity, scalability, maintainability, and better organization.

</details>

**3. How does OOP support scalability?**

<details>
<summary>Show Answer</summary>

OOP allows developers to add new classes and extend existing functionality while minimizing changes to other parts of the program.

</details>

**4. Can one class have multiple objects?**

<details>
<summary>Show Answer</summary>

Yes. A class can be used to create multiple objects, each with its own instance data.

</details>

**5. Can an object exist without a class in Java?**

<details>
<summary>Show Answer</summary>

Every Java object is an instance of a class. Objects are typically created using the `new` keyword.

</details>

**6. Can an object reference be `null`?**

<details>
<summary>Show Answer</summary>

Yes. An object reference can be assigned `null`, which means it does not currently refer to any object.

</details>


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
