
# Module: Inheritance

## 1. Basic Principles of Object-Oriented Programming (OOP)

Object-Oriented Programming (OOP) is a programming approach organized around **objects**, which combine data and behavior.

OOP is built on four fundamental principles:

| Principle | Description |
|:---|:---|
| **Encapsulation** | Bundles data and methods together while controlling access to data. |
| **Abstraction** | Hides implementation details and exposes only essential functionality. |
| **Inheritance** | Allows a class to reuse and extend another class's properties and methods. |
| **Polymorphism** | Allows the same method to behave differently depending on the object. |

<p align="center">
  <img src="https://github.com/user-attachments/assets/33add195-4f94-4be3-9310-cbb894afbcad"
       width="800"
       alt="Four fundamental principles of object-oriented programming">
</p>

<p align="center">
  <sub>
    Image source: Adapted from
    <a href="https://www.geeksforgeeks.org/interview-prep/oops-interview-questions/">GeeksforGeeks – OOP Interview Questions</a>
  </sub>
</p>

---


## 1. Why Do We Need Inheritance?

Let's imagine we are building a school management system. We need to create classes to represent students and teachers.

At first, we might create two separate classes.

### Class 1: Student

```java
public class Student {
    private String name;
    private int age;
    private String address;
    private int studentId;

    public Student(String name, int age, String address, int studentId) {
        this.name = name;
        this.age = age;
        this.address = address;
        this.studentId = studentId;
    }

    public void introduce() {
        System.out.println("Hi, I am " + name);
    }

    public void study() {
        System.out.println(name + " is studying.");
    }
}
```

### Class 2: Teacher

```java
public class Teacher {
    private String name;
    private int age;
    private String address;
    private String subject;

    public Teacher(String name, int age, String address, String subject) {
        this.name = name;
        this.age = age;
        this.address = address;
        this.subject = subject;
    }

    public void introduce() {
        System.out.println("Hi, I am " + name);
    }

    public void teach() {
        System.out.println(name + " is teaching.");
    }
}
```

Do you notice something here?

Both classes have several things in **common**:

- Both have a `name`.
- Both have an `age`.
- Both have an `address`.
- Both have an `introduce()` method.

However, students and teachers also have their own specific information and behaviors:

- A student has a `studentId` and can `study()`.
- A teacher has a `subject` and can `teach()`.

### 1.1. The Problem: Code Duplication

We are writing the same code in multiple classes!

Imagine our school management system grows and we add more types of people, such as administrators, counselors, and teaching assistants.

We would have to repeat the same fields, and common methods in every class.

**But what happens if we need to make a change?**  
  For example:
  - We want to change how the introduce() method works.
  - We want to add a new common field, such as email.

We would have to update every class! That creates unnecessary work and makes our program harder to maintain.

**Can we find a better way?**

Absolutely! This is where **Inheritance** comes into the picture.

### 1.2. The Solution: Inheritance

Instead of repeating common code in every class, we can move the shared fields and methods into a common class called `Person`.

Then, the `Student` and `Teacher` classes can inherit those common features while keeping their own specific fields and methods.

Here is what we are going to do:

1. Superclass (Parent Class): Create a common parent class called `Person` containing shared fields and methods.
2. Subclass (Child Class): Create child classes called `Student` and `Teacher` that reuse the functionality of `Person`.


### 1.3. Creating the Parent Class

Let's move the common fields and methods into a single `Person` class.

```java
public class Person {
    protected String name;
    protected int age;
    protected String address;

    public Person() {

    }

    public void introduce() {
        System.out.println("Hi, I am " + name);
    }
}
```
Now, the common information and behavior are defined in one place.
**Note:** Person() is a no-argument constructor because it does not accept any parameters. Java automatically calls this constructor when a child class is created and its constructor does not explicitly call another parent constructor. We will see this when creating Student and Teacher objects.

**Understanding `protected`:** The protected modifier allows `Student` and `Teacher` to directly access the inherited name, age, and address fields. It also allows access from other classes in the same package.

### 1.4. Creating Child Classes

Next, let's create the `Student` and `Teacher` classes.

**Student class:**

```java
public class Student extends Person {
    private int studentId;

    public Student(String name, int age, String address, int studentId) {
        this.name = name;
        this.age = age;
        this.address = address;
        this.studentId = studentId;
    }

    public void study() {
        System.out.println(name + " is studying.");
    }
}
```

**Teacher class:**

```java
public class Teacher extends Person {
    private String subject;

    public Teacher(String name, int age, String address, String subject) {
        this.name = name;
        this.age = age;
        this.address = address;
        this.subject = subject;
    }

    public void teach() {
        System.out.println(name + " is teaching.");
    }
}
```

Look closely at this line:

```java
public class Student extends Person
```

The `extends` keyword tells Java that `Student` inherits from `Person`.

Similarly, `Teacher` inherits from `Person`.

This means both child classes can reuse the accessible fields and methods of the parent class.

### 1.5. Creating Objects

Now, let's create objects of both classes.

```java
// Create a Student object
Student student = new Student("Alex", 20, "Dallas", 1001);

student.introduce(); // Inherited from Person
student.study();     // Defined in Student

// Create a Teacher object
Teacher teacher = new Teacher(
    "Dr. Smith", 40, "Austin", "Computer Science"
);

teacher.introduce(); // Inherited from Person
teacher.teach();     // Defined in Teacher
```

Notice that we can call `introduce()` on both objects even though we defined it only once in the `Person` class.
We do not need to rewrite the same method in `Student` and `Teacher`!

**What happens when we create a Student object?**

When we execute:
Student student = new Student("Alex", 20, "Dallas", 1001);

Java automatically calls the no-argument constructor of the parent class, Person(), before executing the Student constructor.

This allows the child class to be created without explicitly calling the parent constructor.

### 1.6. Why Is Inheritance Useful?

**Inheritance helps us:**

1. **Reuse code:** Share common fields and methods between related classes.
2. **Reduce duplication:** Avoid writing the same code repeatedly.
3. **Improve maintainability:** Make changes to common functionality in one place.
4. **Extend functionality:** Allow child classes to add their own fields and methods.

This is the main idea behind inheritance: **one class can reuse and extend the functionality of another class.**

### Real-World Example: Vehicles

<p align="center">
  <img src="https://github.com/user-attachments/assets/4a843286-4361-41da-95bb-5d009fa0365e"
       width="700"
       alt="Vehicle inheritance example showing relationships between classes">
</p>

<p align="center">
  <sub>
    Image source:
    <a href="https://takeuforward.org/blogs/oops/what-is-oops">
      TakeUForward – What is OOPs?
    </a>
  </sub>
</p>

Think about different types of vehicles. A car and a bike share common characteristics, but each also has unique features.

<AsyncImage query="simple educational illustration car motorcycle bicycle truck different types of vehicles white background" aspectRatio="16:9" width="100%" fit="contain"/>

**Important:** Constructors are not inherited in Java. However, a subclass can call a superclass constructor using `super()`.

## 4. Types of Inheritance

The following diagram illustrates the five common types of inheritance.

<img width="1042" height="745" alt="image" src="https://github.com/user-attachments/assets/0f511a15-2999-47e1-9e68-fcbcf0feb57a" />
<p align="center">
  <sub>
    Image source: Adapted from
    <a href="https://www.geeksforgeeks.org/interview-prep/oops-interview-questions/">GeeksforGeeks – OOP Interview Questions</a>
  </sub>
</p>

**Note:** Java supports single, multilevel, and hierarchical inheritance through classes. **Multiple** and **hybrid** inheritance are not supported through classes alone. However, interfaces allow Java to support multiple inheritance of type and create hybrid inheritance structures.



### 4.1 Single Inheritance

A subclass inherits from one superclass.

<AsyncImage query="single inheritance UML diagram Animal parent Dog child simple educational diagram" aspectRatio="16:9" width="100%" fit="contain"/>

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating.");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking.");
    }
}
```

**Example:** `Dog` inherits from `Animal`.

### 4.2 Multilevel Inheritance

A class inherits from another subclass, forming an inheritance chain.

<AsyncImage query="multilevel inheritance UML diagram Animal Mammal Dog three levels educational" aspectRatio="16:9" width="100%" fit="contain"/>

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating.");
    }
}

class Mammal extends Animal {
    void walk() {
        System.out.println("Mammal is walking.");
    }
}

class Dog extends Mammal {
    void bark() {
        System.out.println("Dog is barking.");
    }
}
```

**Example:** `Dog` inherits from `Mammal`, and `Mammal` inherits from `Animal`. Therefore, `Dog` can access the inherited methods from both parent classes, subject to access rules.

### 4.3 Hierarchical Inheritance

Multiple subclasses inherit from the same superclass.

<AsyncImage query="hierarchical inheritance UML diagram Vehicle parent Car Bike Truck child classes" aspectRatio="16:9" width="100%" fit="contain"/>

```java
class Vehicle {
    void start() {
        System.out.println("Vehicle is starting.");
    }
}

class Car extends Vehicle {
    void drive() {
        System.out.println("Car is driving.");
    }
}

class Bike extends Vehicle {
    void ride() {
        System.out.println("Bike is riding.");
    }
}
```

**Example:** Both `Car` and `Bike` inherit from `Vehicle`.

### 4.4 Multiple Inheritance

Multiple inheritance occurs when one class inherits from more than one parent class.

**Java does not support multiple inheritance with classes.**

For example, the following code is illegal:

```java
class A { }
class B { }

// Not allowed in Java
class C extends A, B { }
```
Java avoids this restriction to prevent ambiguity and complexity, such as the **Diamond Problem**.

### The Diamond Problem

The Diamond Problem occurs when two parent classes inherit from the same superclass and provide their own versions of an inherited method. The child class may not know which method to use.

Java avoids this problem with classes, but similar ambiguity can occur with interfaces that have default methods.

<img width="275" height="335" alt="image" src="https://github.com/user-attachments/assets/7bd07e35-a987-4d7c-819d-f73ed7ffafca" />


**Java Example: Diamond Problem**

```java
interface A {
    default void whoAmI() {
        System.out.println("Interface A");
    }
}

interface B extends A {
    @Override
    default void whoAmI() {
        System.out.println("Interface B");
    }
}

interface C extends A {
    @Override
    default void whoAmI() {
        System.out.println("Interface C");
    }
}

class D implements B, C {
    @Override
    public void whoAmI() {
        System.out.println("Class D");

        B.super.whoAmI();
    }
}

public class Main {
    public static void main(String[] args) {
        D obj = new D();
        obj.whoAmI();
    }
}
```

**Output:**

```text
Class D
Interface B
```

### Understanding the Example

- `A` is the common parent interface.
- `B` and `C` both extend `A` and override `whoAmI()`.
- `D` implements both `B` and `C`.
- `D` overrides `whoAmI()` to resolve the ambiguity.
- `B.super.whoAmI()` explicitly calls the method from interface `B`.

**Key Idea:** Java does not allow a class to extend multiple classes, but it allows a class to implement multiple interfaces. When default methods conflict, the class must resolve the conflict.


However, Java supports multiple inheritance of type through **interfaces**, which will be covered in a later module.

### 4.5 Hybrid Inheritance

Hybrid inheritance combines two or more types of inheritance.

Java does not support hybrid inheritance through classes alone. However, combinations of class inheritance and interfaces can be used to achieve hybrid inheritance structures.

### Summary of Inheritance Types

| Type | Description | Supported in Java? |
|:---|:---|:---|
| Single | One subclass inherits from one superclass. | Yes |
| Multilevel | A class inherits from a subclass, forming a chain. | Yes |
| Hierarchical | Multiple subclasses inherit from one superclass. | Yes |
| Multiple | One class inherits from multiple parent classes. | No, not with classes |
| Hybrid | Combines two or more inheritance types. | Through classes and interfaces |

## 5. The `super` Keyword

The `super` keyword refers to the immediate parent class of a subclass.

It is commonly used for two purposes:

1. **`super()`** – Calls the parent class constructor.
2. **`super.methodName()`** – Calls a method from the parent class.

### 4.1 Calling a Parent Constructor with `super()`

When a subclass object is created, the parent class constructor must also execute to initialize the inherited portion of the object.

The `super()` statement calls the parent class constructor.

**Example:**

```java
class Person {
    protected String name;
    protected int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

class Student extends Person {
    private int studentId;

    public Student(String name, int age, int studentId) {
        super(name, age); // Calls the Person constructor
        this.studentId = studentId;
    }
}
```

In this example:
- `Person` is the parent class.
- `Student` is the child class.
- `super(name, age)` calls the `Person` constructor.
- `studentId` is initialized by the `Student` constructor.

**Important:** A call to `super()` must be the first statement in a constructor. If the parent class has no accessible no-argument constructor, the child constructor must explicitly call an appropriate parent constructor.

### 4.2 Calling a Parent Method with `super`

A subclass can use `super.methodName()` to call a method defined in its parent class.

```java
class Animal {
    public void makeSound() {
        System.out.println("The animal makes a sound.");
    }
}

class Dog extends Animal {
    public void makeSound() {
        super.makeSound(); // Calls the parent method
        System.out.println("The dog barks.");
    }
}
```

**Output:**

```text
The animal makes a sound.
The dog barks.
```

## 5. Method Overriding

Sometimes, a subclass needs to provide a different implementation of an inherited method.

**Method overriding** occurs when a subclass provides its own implementation of a method already defined in its parent class.

The overriding method must have the same method name and parameter list, along with a compatible return type.

Java provides the `@Override` annotation to indicate that a method is intended to override a parent class method. The compiler checks that the override is valid.

### Example: Animal and Cat

```java
// Parent Class
class Animal {
    public void makeSound() {
        System.out.println("The animal makes a sound.");
    }
}

// Child Class
class Cat extends Animal {

    @Override
    public void makeSound() {
        System.out.println("The cat meows: Meow! Meow!");
    }
}
```

### Using Method Overriding

```java
public class Main {
    public static void main(String[] args) {

        Animal animal = new Animal();
        Cat cat = new Cat();

        animal.makeSound();
        cat.makeSound();
    }
}
```

**Output:**

```text
The animal makes a sound.
The cat meows: Meow! Meow!
```

### Understanding Method Overriding

- The `Animal` class defines the original `makeSound()` method.
- The `Cat` class inherits from `Animal`.
- The `Cat` class overrides `makeSound()` with its own implementation.
- The `@Override` annotation helps the compiler verify that the method correctly overrides an inherited method.

**Key Idea:** Method overriding allows subclasses to customize inherited behavior.

## 6. Complete Code Example: Person and Student

The following example combines inheritance, constructors, the `super` keyword, method overriding, and object creation.

Save the following code in a file named `Main.java`.

```java
// Superclass (Parent Class)
class Person {
    protected String name;
    protected int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}

// Subclass (Child Class)
class Student extends Person {
    private double gpa;

    public Student(String name, int age, double gpa) {
        super(name, age); // Call the parent constructor
        this.gpa = gpa;
    }

    // Override the parent's displayInfo() method
    @Override
    public void displayInfo() {
        super.displayInfo(); // Call the parent method
        System.out.println("GPA: " + gpa);
    }
}

// Main Class
public class Main {
    public static void main(String[] args) {

        // Create a Student object
        Student student = new Student("Alex Smith", 20, 3.85);

        // Call the overridden method
        student.displayInfo();
    }
}
```

**Output:**

```text
Name: Alex Smith
Age: 20
GPA: 3.85
```

### Understanding the Complete Example

| Component | Purpose |
|:---|:---|
| `Person` | Parent class containing common fields and methods. |
| `Student extends Person` | Inherits the fields and methods of `Person`. |
| `protected name` and `age` | Allow access within the same package and through subclasses. |
| `private gpa` | Stores student-specific data. |
| `super(name, age)` | Calls the parent constructor to initialize inherited fields. |
| `@Override` | Indicates that `displayInfo()` overrides the parent method. |
| `super.displayInfo()` | Calls the parent version of `displayInfo()`. |

## 7. Benefits of Inheritance

| Benefit | Explanation |
|:---|:---|
| **Code Reusability** | Common fields and methods are defined once in a superclass and reused by subclasses. |
| **Extensibility** | New functionality can be added to subclasses without modifying the parent class. |
| **Method Overriding** | Subclasses can customize inherited behavior. |
| **Maintainability** | Shared functionality is centralized, making updates easier to manage. |
| **Organization** | Establishes clear relationships between related classes. |

---

## 8. Quick Review

**1. What is inheritance?**

<details>
<summary>Show Answer</summary>

Inheritance allows one class to acquire fields and methods from another class. It promotes code reuse and establishes relationships between classes.

</details>

**2. What keyword is used in Java to implement inheritance?**

<details>
<summary>Show Answer</summary>

The `extends` keyword.

</details>

**3. What is the difference between a superclass and a subclass?**

<details>
<summary>Show Answer</summary>

A superclass (parent class) is the class whose features are inherited. A subclass (child class) inherits those features and can add its own fields and methods.

</details>

**4. What is an is-a relationship?**

<details>
<summary>Show Answer</summary>

An is-a relationship describes how a subclass represents a specific type of its superclass. For example, a Car is a Vehicle.

</details>

**5. What is the purpose of the `super` keyword?**

<details>
<summary>Show Answer</summary>

The `super` keyword refers to the immediate parent class. It can be used to call the parent constructor using `super()` or access a parent method using `super.methodName()`.

</details>

**6. What is method overriding?**

<details>
<summary>Show Answer</summary>

Method overriding occurs when a subclass provides its own implementation of a method already defined in its parent class.

</details>

**7. Why is the `@Override` annotation used?**

<details>
<summary>Show Answer</summary>

It tells the compiler that a method is intended to override a parent class method and helps detect errors in the method declaration.

</details>

**8. Does Java support multiple inheritance with classes?**

<details>
<summary>Show Answer</summary>

No. A Java class can extend only one superclass. However, Java supports multiple inheritance of type through interfaces.

</details>

**9. Are constructors inherited by subclasses?**

<details>
<summary>Show Answer</summary>

No. Constructors are not inherited. However, a subclass constructor can call a superclass constructor using `super()`.

</details>

**10. What is the difference between method overriding and method overloading?**

<details>
<summary>Show Answer</summary>

Method overriding occurs when a subclass provides a new implementation of an inherited method. Method overloading occurs when multiple methods in the same class have the same name but different parameter lists.

</details>

---
