# Abstract Classes in Java

## Object-Oriented Programming (OOP) Review

Object-Oriented Programming (OOP) is a programming approach organized around **objects**, which combine data and behavior.

OOP is built on four fundamental principles:

| **Principle** | **Description** |
|---|---|
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

In this module, we will focus on **Abstraction** and learn how Java uses abstract classes to implement it.

---

## 1. Introduction to Abstraction

In previous modules, we explored inheritance and method overloading. We learned how classes can inherit fields and methods from other classes and customize their behavior.

**Real-world example: Driving a Car**

A person can drive a car using the steering wheel, brakes, and accelerator without understanding how the engine or other internal components work.

<p align="center">
  <img src="https://github.com/user-attachments/assets/5115b926-4d76-4cf0-9930-9b2f308298fc"
       width="700"
       alt="Car illustrating the concept of abstraction">
</p>

<p align="center">
  <sub>
    Image source:
    <a href="https://takeuforward.org/blogs/oops/what-is-oops">TakeUForward – What is OOPs?</a>
  </sub>
</p>

**Key Idea:** Focus on *what an object does*, rather than *how it works internally*.

Sometimes, however, a parent class represents a concept that is too general to create objects directly.

For example:

- An `Animal` class represents different animals, but each animal makes a different sound.
- A `Shape` class represents different shapes, but each shape calculates its area differently.

How can we define common features while allowing each child class to provide its own implementation?

Java provides **abstraction** to solve this problem.

**Abstraction** is an OOP principle that hides implementation details and exposes only essential functionality.

Java supports abstraction through two mechanisms:

1. **Abstract Classes:** Can combine abstract methods with fully implemented methods.
2. **Interfaces:** Define a contract that implementing classes must follow.

We will focus on abstract classes in this chapter and study interfaces in a later module.

## 2. What Is an Abstract Class?

An **abstract class** is a class declared with the `abstract` keyword. It cannot be instantiated directly, but it can be used as a parent class for other classes.

Abstract classes provide a common structure for related subclasses.

### Declaring an Abstract Class

```java
abstract class ClassName {
    // Fields
    // Constructors
    // Abstract methods
    // Regular methods
}
```

**Example:**

```java
// Abstract class
public abstract class Vehicle {

    protected String brand;

    public Vehicle(String brand) {
        this.brand = brand;
    }

    // Concrete method
    public void turnOnEngine() {
        System.out.println("The engine is running.");
    }

    // Abstract method
    public abstract void start();
}
```

### Understanding the Example

| Component | Purpose |
|---|---|
| `abstract class Vehicle` | Declares an abstract class. |
| `brand` | A field shared by subclasses. |
| `Vehicle()` | Constructor that initializes the brand. |
| `turnOnEngine()` | A concrete method with an implementation. |
| `start()` | An abstract method without a body. |

**Important:** You cannot create an object directly from an abstract class.

```java
// Not allowed
Vehicle vehicle = new Vehicle("Toyota");
```

However, you can create objects of concrete subclasses that extend it.

## 3. Abstract Methods

An **abstract method** is a method declared without a body. It defines what a subclass must do, but does not specify how to do it.

Abstract methods:

- Use the `abstract` keyword.
- Do not contain a method body.
- End with a semicolon.
- Must be implemented by concrete subclasses.

**Syntax:**

```java
public abstract void methodName();
```

**Example:**

```java
abstract class Animal {

    // Abstract method
    public abstract void makeSound();

    // Concrete method
    public void sleep() {
        System.out.println("Animal is sleeping.");
    }
}
```

In this example:

- `makeSound()` is abstract because it has no implementation.
- `sleep()` is concrete because it has a method body.

### Implementing Abstract Methods

A concrete subclass must provide an implementation for every inherited abstract method.

```java
class Dog extends Animal {

    @Override
    public void makeSound() {
        System.out.println("Dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {

        Dog dog = new Dog();

        dog.makeSound();
        dog.sleep();
    }
}
```

**Output:**

```text
Dog barks.
Animal is sleeping.
```

The `Dog` class provides its own implementation of `makeSound()`, while inheriting the `sleep()` method from `Animal`.

**Note:** If a subclass does not implement all inherited abstract methods, it must also be declared `abstract`.

## 4. Abstract Classes vs. Regular Classes

| Feature | Regular Class | Abstract Class |
|---|---|---|
| Instantiation | Can create objects using `new`. | Cannot be instantiated directly. |
| Methods | Contains implemented methods. | Can contain abstract and concrete methods. |
| Fields | Can contain fields. | Can contain fields. |
| Constructors | Can have constructors. | Can have constructors. |
| Inheritance | Can be extended. | Can be extended. |
| Purpose | Creates usable objects. | Provides a common structure for subclasses. |

**Important:** An abstract class does not have to contain abstract methods. It can contain only regular methods and still be abstract.

## 5. Rules of Abstract Classes

Remember these important rules:

1. An abstract class must use the `abstract` keyword.
2. An abstract class cannot be instantiated directly.
3. An abstract class can contain constructors, fields, and regular methods.
4. An abstract method cannot have a method body.
5. If a class contains an abstract method, the class must also be declared `abstract`.
6. A concrete subclass must implement all inherited abstract methods.
7. If a subclass does not implement all inherited abstract methods, it must also be declared `abstract`.
8. An abstract class can extend another class, including another abstract class.

## 6. Complete Code Example: Shape Hierarchy

Let's create an abstract `Shape` class with two subclasses: `Circle` and `Rectangle`.

Each shape has a color, but each calculates its area differently.

### Complete Java Program

Save the following code in a file named `Main.java`.

```java
// Abstract Superclass
abstract class Shape {

    protected String color;

    public Shape(String color) {
        this.color = color;
    }

    // Concrete method
    public void displayColor() {
        System.out.println("Shape color: " + color);
    }

    // Abstract method
    public abstract double calculateArea();
}

// Concrete Subclass 1
class Circle extends Shape {

    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Concrete Subclass 2
class Rectangle extends Shape {

    private double width;
    private double height;

    public Rectangle(String color, double width, double height) {
        super(color);
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

// Main Class
public class Main {

    public static void main(String[] args) {

        // Cannot instantiate an abstract class
        // Shape s = new Shape("Red");

        // Create objects of concrete subclasses
        Shape circle = new Circle("Red", 5.0);
        Shape rectangle = new Rectangle("Blue", 4.0, 6.0);

        circle.displayColor();
        System.out.println("Circle Area: " + circle.calculateArea());

        System.out.println();

        rectangle.displayColor();
        System.out.println("Rectangle Area: " + rectangle.calculateArea());
    }
}
```

### Output

```text
Shape color: Red
Circle Area: 78.53981633974483

Shape color: Blue
Rectangle Area: 24.0
```

### Understanding the Example

| Component | Purpose |
|---|---|
| `Shape` | Abstract parent class. |
| `color` | Common field inherited by subclasses. |
| `Shape()` | Constructor that initializes the color. |
| `displayColor()` | Concrete method shared by all shapes. |
| `calculateArea()` | Abstract method that subclasses must implement. |
| `Circle` | Calculates area using π × radius². |
| `Rectangle` | Calculates area using width × height. |
| `@Override` | Indicates that a subclass is implementing an inherited abstract method. |
| `super(color)` | Calls the parent class constructor. |

**Key Idea:** The abstract `Shape` class defines what all shapes have in common, while each subclass provides its own implementation of `calculateArea()`.

## 7. Constructors in Abstract Classes

Abstract classes can have constructors, even though they cannot be instantiated directly.

A constructor in an abstract class initializes fields that are inherited by its subclasses.

**Example:**

```java
abstract class Animal {

    protected String name;

    public Animal(String name) {
        this.name = name;
    }
}

class Dog extends Animal {

    public Dog(String name) {
        super(name);
    }

    public void display() {
        System.out.println("Dog name: " + name);
    }
}

public class Main {
    public static void main(String[] args) {

        Dog dog = new Dog("Buddy");
        dog.display();
    }
}
```

**Output:**

```text
Dog name: Buddy
```

The `Dog` constructor calls `super(name)` to initialize the `name` field through the parent class constructor.

## 8. Benefits of Abstract Classes

| Benefit | Explanation |
|---|---|
| Code Reusability | Common fields and methods can be shared among subclasses. |
| Enforced Design | Requires concrete subclasses to implement specified abstract methods. |
| Organization | Provides a common structure for related classes. |
| Partial Abstraction | Combines abstract methods with fully implemented methods. |

## 9. Abstract Classes vs. Interfaces

Java provides both abstract classes and interfaces to support abstraction.

We will study interfaces in a later module. For now, understand their basic differences.

| Feature | Abstract Class | Interface |
|---|---|---|
| Keyword | `abstract class` | `interface` |
| Inheritance | A class can extend only one class. | A class can implement multiple interfaces. |
| Fields | Can have instance fields. | Fields are automatically `public static final`. |
| Constructors | Can have constructors. | Cannot have constructors. |
| Methods | Can have abstract and concrete methods. | Can have abstract, default, and static methods. |

### When to Use an Abstract Class?

Use an abstract class when several related classes share common fields, methods, and behavior.

For example, `Circle` and `Rectangle` can share a `Shape` parent class.

**Note:** Interfaces can also contain implemented methods, such as `default` and `static` methods. Therefore, the traditional description of interfaces as providing "100% abstraction" is a simplification.

## 10. Quick Review

**1. What are the four fundamental principles of OOP?**

<details>
<summary>Show Answer</summary>

Encapsulation, Abstraction, Inheritance, and Polymorphism.

</details>

**2. What is abstraction in Java?**

<details>
<summary>Show Answer</summary>

Abstraction hides implementation details and exposes only essential functionality.

</details>

**3. What is an abstract class?**

<details>
<summary>Show Answer</summary>

An abstract class is a class declared using the `abstract` keyword. It cannot be instantiated directly and is designed to serve as a parent class for other classes.

</details>

**4. Can you create an object of an abstract class using `new`?**

<details>
<summary>Show Answer</summary>

No. Abstract classes cannot be instantiated directly. You must create objects of concrete subclasses.

</details>

**5. What is an abstract method?**

<details>
<summary>Show Answer</summary>

An abstract method is a method declared without a body. It must be implemented by a concrete subclass.

</details>

**6. Can an abstract class contain regular methods?**

<details>
<summary>Show Answer</summary>

Yes. An abstract class can contain both abstract methods and fully implemented methods.

</details>

**7. Can an abstract class have a constructor?**

<details>
<summary>Show Answer</summary>

Yes. Its constructor initializes fields when a subclass object is created.

</details>

**8. What happens if a subclass does not implement all inherited abstract methods?**

<details>
<summary>Show Answer</summary>

The subclass must also be declared `abstract`. Otherwise, the compiler reports an error.

</details>

**9. Does an abstract class always need at least one abstract method?**

<details>
<summary>Show Answer</summary>

No. An abstract class can have no abstract methods and still cannot be instantiated directly.

</details>

**10. What is the purpose of the `@Override` annotation?**

<details>
<summary>Show Answer</summary>

It tells Java that a method is intended to override or implement an inherited method. The compiler checks that the method correctly overrides the parent method.

</details>

### Review Questions

**1. How is abstraction achieved in Java?**

<details>
<summary>Show Answer</summary>

Using **abstract classes** and **interfaces**.

</details>

**2. Can we create an object of an abstract class?**

<details>
<summary>Show Answer</summary>

No. Abstract classes cannot be instantiated directly.

</details>

**3. Can abstract classes have concrete methods?**

<details>
<summary>Show Answer</summary>

---

## References

- [Oracle Java Tutorials – Abstract Methods and Classes](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)
- [Abstraction and Abstract Classes – Medium](https://medium.com/@marvelahrun/abstraction-and-abstract-classes-a7cba4022c9f)

Yes. Abstract classes can contain both abstract methods (without a body) and concrete methods (with a body).

</details>

---
