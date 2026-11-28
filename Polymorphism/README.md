
# Basic Principles of Object-Oriented Programming (OOP)

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


## Polymorphism

The word **polymorphism** comes from Greek: *poly* ("many") and *morph* ("forms").
In programming, polymorphism means **"one interface, multiple implementations."** It allows different objects to respond to the same method call in different ways.

### Real-World Example: Animal Sounds

A method named `makeSound()` can produce different results depending on the animal:

- A `Dog` barks.
- A `Cat` meows.
- A `Bird` chirps.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e8a87f53-9595-456c-823e-406f260346fb"
       width="700"
       alt="Animal sounds illustrating polymorphism">
</p>

### Key Idea

The same method call can produce different behaviors for different objects.

### Types of Polymorphism

Java supports two types of polymorphism:

<img width="1264" height="842" alt="image" src="https://github.com/user-attachments/assets/884a99ba-595c-4f21-aeee-9501dc49386c" />


* **Method Overloading (Compile-Time / Static Polymorphism):**
  * Same method name, **different signature** (parameter list)
  * **Inheritance required?** No (happens within the same class)
  * The compiler determines which overloaded method to call.
  * *Example:* A class having multiple constructors (`Printer()`, `Printer(String name)`)
* **Method Overriding (Run-Time / Dynamic Polymorphism):**
  * Same method name, **same signature**
  * **Inheritance required?** Yes (subclass redefines a superclass method)
  * The JVM determines which overridden method to execute based on the actual object.
  * *Example:* A subclass customizing `toString()` or `equals()`


---


##23. Compile-Time Polymorphism (Method Overloading)

**Compile-time polymorphism** occurs when a class has multiple methods with the same name but different parameter lists.

Java determines which overloaded method to call during compilation based on the arguments provided.

### How Method Overloading Works

The compiler looks for the most appropriate matching method based on:

1. **Exact Match:** The parameter types match the arguments.
2. **Widening Conversion:** Java can automatically convert a smaller primitive type to a larger compatible type, such as `int` to `double`.
3. **Other Conversions:** Java can also consider boxing, unboxing, and other applicable conversions.

If the compiler cannot determine a valid, unambiguous method, it reports a compilation error.

### Example: Method Overloading

```java
class Printer {

    public void print(int x) {
        System.out.println("Printing integer: " + x);
    }

    public void print(double x) {
        System.out.println("Printing double: " + x);
    }

    public void print(String text) {
        System.out.println("Printing string: " + text);
    }
}

public class Main {
    public static void main(String[] args) {

        Printer p = new Printer();

        p.print(42);
        p.print(3.14);
        p.print("Hello");
    }
}
```

**Output:**

```text
Printing integer: 42
Printing double: 3.14
Printing string: Hello
```

### Explanation

| Method Call | Selected Method | Reason |
|---|---|---|
| `p.print(42)` | `print(int)` | Exact match |
| `p.print(3.14)` | `print(double)` | Exact match |
| `p.print("Hello")` | `print(String)` | Exact match |

**Key Point:** Method overloading allows multiple methods to share the same name while accepting different parameters.

---

## 3. Runtime Polymorphism (Method Overriding)

**Runtime polymorphism** occurs when a subclass provides its own implementation of a method inherited from a superclass.

Java determines which overridden method to execute at runtime based on the actual object.

This is also called **Dynamic Binding** or **Late Binding**.

### Example: Method Overriding

```java
class Animal {

    public void makeSound() {
        System.out.println("Animal makes a sound.");
    }
}

class Dog extends Animal {

    @Override
    public void makeSound() {
        System.out.println("Dog barks.");
    }
}

class Cat extends Animal {

    @Override
    public void makeSound() {
        System.out.println("Cat meows.");
    }
}

public class Main {
    public static void main(String[] args) {

        Dog dog = new Dog();
        Cat cat = new Cat();

        dog.makeSound();
        cat.makeSound();
    }
}
```

**Output:**

```text
Dog barks.
Cat meows.
```

### Explanation

- `Dog` and `Cat` inherit from `Animal`.
- Both subclasses override the `makeSound()` method.
- Each subclass provides its own implementation.

The same method name produces different behaviors depending on the object.

---

## 4. Upcasting and Dynamic Method Dispatch

### What Is Upcasting?

**Upcasting** means assigning a subclass object to a superclass reference variable.

For example:

```java
Animal myAnimal = new Dog();
```

Here:

- `Animal` is the reference type.
- `Dog` is the actual object type.
- The `Dog` object is assigned to an `Animal` reference.

This is allowed because a `Dog` is an `Animal`.

### Understanding Dynamic Method Dispatch

When an overridden method is called through a superclass reference, Java executes the method belonging to the actual object at runtime.

This mechanism is called **Dynamic Method Dispatch**.

```java
class Animal {

    public void makeSound() {
        System.out.println("Animal makes a sound.");
    }
}

class Dog extends Animal {

    @Override
    public void makeSound() {
        System.out.println("Dog barks.");
    }
}

class Cat extends Animal {

    @Override
    public void makeSound() {
        System.out.println("Cat meows.");
    }
}

public class Main {
    public static void main(String[] args) {

        Animal animal1 = new Dog();
        Animal animal2 = new Cat();

        animal1.makeSound();
        animal2.makeSound();
    }
}
```

**Output:**

```text
Dog barks.
Cat meows.
```

### Important: Reference Type vs. Object Type

| Term | Meaning |
|---|---|
| Reference Type | Determines which methods and fields can be accessed through the variable. |
| Object Type | Determines which overridden instance method executes at runtime. |

**Remember:** The reference type controls access, while the actual object type determines the overridden method that runs.

---

## 5. Complete Code Example: Notification System

This example combines **abstract classes, inheritance, method overriding, and runtime polymorphism**.

### Complete Code

Save the following code in a file named `Main.java`.

```java
// Abstract Superclass
abstract class Notification {

    protected String recipient;

    public Notification(String recipient) {
        this.recipient = recipient;
    }

    public abstract void send();
}

// Subclass 1: Email
class EmailNotification extends Notification {

    public EmailNotification(String recipient) {
        super(recipient);
    }

    @Override
    public void send() {
        System.out.println("Sending EMAIL to " + recipient);
    }
}

// Subclass 2: SMS
class SMSNotification extends Notification {

    public SMSNotification(String recipient) {
        super(recipient);
    }

    @Override
    public void send() {
        System.out.println("Sending SMS text message to " + recipient);
    }
}

// Subclass 3: Push Notification
class PushNotification extends Notification {

    public PushNotification(String recipient) {
        super(recipient);
    }

    @Override
    public void send() {
        System.out.println("Sending Push Notification to device: " + recipient);
    }
}

public class Main {

    public static void main(String[] args) {

        // Array of parent-class references
        Notification[] notifications = new Notification[3];

        notifications[0] = new EmailNotification("student@angelo.edu");
        notifications[1] = new SMSNotification("555-0199");
        notifications[2] = new PushNotification("UserDevice_X99");

        // Runtime polymorphism
        for (Notification n : notifications) {
            n.send();
            System.out.println("-----------------------------------");
        }
    }
}
```

### Output

```text
Sending EMAIL to student@angelo.edu
-----------------------------------
Sending SMS text message to 555-0199
-----------------------------------
Sending Push Notification to device: UserDevice_X99
-----------------------------------
```

### Understanding the Code

| Code | Explanation |
|---|---|
| `abstract class Notification` | Defines a common parent class. |
| `protected String recipient` | Stores the notification recipient. |
| `public abstract void send()` | Requires subclasses to implement `send()`. |
| `extends Notification` | Creates a subclass that inherits from `Notification`. |
| `super(recipient)` | Calls the parent-class constructor. |
| `@Override` | Indicates that a subclass overrides the inherited method. |
| `Notification[]` | Creates an array that stores references to different notification objects. |
| `n.send()` | Executes the appropriate overridden method at runtime. |

### How Runtime Polymorphism Works

1. The `Notification` class defines the common `send()` method.
2. Each subclass provides its own implementation.
3. The array stores different notification objects using the same parent reference type.
4. The `for` loop calls `send()` on each object.
5. Java executes the correct subclass implementation at runtime.

**Key Idea:** One parent-class reference type can work with many different child objects.

---

## 7. Benefits of Polymorphism

| Benefit | Explanation |
|---|---|
| Code Flexibility | Allows methods to work with different object types through a common parent type. |
| Extensibility | New subclasses can be added without rewriting existing code that uses the parent type. |
| Loose Coupling | Code can depend on a common parent type rather than specific classes. |
| Cleaner Code | Reduces the need for complicated `if-else` or `switch` statements to handle different object types. |
| Code Reusability | Allows common code to work with multiple related classes. |

---

## 8. Quick Review

**1. What does polymorphism mean in object-oriented programming?**

<details>
<summary>Show Answer</summary>

Polymorphism means "many forms." It allows different classes to respond to the same method call with their own implementations.

</details>

**2. What are the two types of polymorphism in Java?**

<details>
<summary>Show Answer</summary>

- Compile-time polymorphism (method overloading).
- Runtime polymorphism (method overriding).

</details>

**3. What is compile-time polymorphism?**

<details>
<summary>Show Answer</summary>

It occurs when multiple methods have the same name but different parameter lists. The compiler determines which method to call.

</details>

**4. What is runtime polymorphism?**

<details>
<summary>Show Answer</summary>

It occurs when a subclass overrides an inherited method. Java determines which overridden method to execute at runtime based on the actual object.

</details>

**5. What is upcasting?**

<details>
<summary>Show Answer</summary>

Upcasting means assigning a subclass object to a superclass reference variable.

Example:

```java
Animal animal = new Dog();
```

</details>

**6. What is Dynamic Method Dispatch?**

<details>
<summary>Show Answer</summary>

It is the mechanism Java uses to select the overridden method at runtime based on the actual object type.

</details>

**7. What is the difference between a reference type and an object type?**

<details>
<summary>Show Answer</summary>

The reference type determines which members can be accessed. The actual object type determines which overridden instance method executes.

</details>

**8. Can a parent-class reference refer to different child objects?**

<details>
<summary>Show Answer</summary>

Yes. For example:

```java
Animal a1 = new Dog();
Animal a2 = new Cat();
```

Both objects can be referenced using the `Animal` type.

</details>

**9. How does polymorphism make programs easier to maintain?**

<details>
<summary>Show Answer</summary>

It allows common code to work with different related objects. New subclasses can be added without changing existing code that uses the parent type.

</details>

**10. How does polymorphism support extensibility?**

<details>
<summary>Show Answer</summary>

New classes can provide their own implementations of methods without changing the code that uses the common parent class or interface.

</details>

---
