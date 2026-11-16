https://users.cs.utah.edu/~germain/PPS/Topics/interfaces.html


# Interfaces in Java

## 1. Introduction to Interfaces

An **interface** in Java is a blueprint that defines a set of methods a class must implement.

It specifies **what a class should do**, but generally does not define how the class performs those actions.

Think of an interface as a contract: any class that implements the interface agrees to provide implementations for its required methods.

### Real-World Example: USB Connection

A USB port provides a standard connection that different devices can use.

- A keyboard uses the connection to send input.
- A mouse uses the connection to send movement information.
- A printer uses the connection to receive printing instructions.

Different devices follow the same connection standard but perform different tasks.

### Key Idea

An interface defines common behavior, while each implementing class provides its own implementation.

---

## 2. Creating an Interface

Java uses the `interface` keyword to declare an interface.

### Syntax

```java
interface InterfaceName {

    // Abstract methods
    void methodName();
}
```

A class uses the `implements` keyword to implement an interface.

### Example: Animal Interface

```java
interface Animal {

    void makeSound();
}

class Dog implements Animal {

    @Override
    public void makeSound() {
        System.out.println("Dog barks.");
    }
}

public class Main {

    public static void main(String[] args) {

        Dog dog = new Dog();
        dog.makeSound();
    }
}
```

**Output:**

```text
Dog barks.
```

### Explanation

- `interface Animal` declares an interface.
- `makeSound()` defines a method the implementing class must provide.
- `implements Animal` means `Dog` agrees to follow the interface.
- `@Override` indicates that `Dog` provides its implementation of `makeSound()`.

**Important:** Interface methods without a body are implicitly `public abstract`. Therefore, the implementing method must be declared `public`.

---

## 3. Important Rules of Interfaces

Java interfaces follow several important rules:

1. An interface is declared using the `interface` keyword.
2. An interface cannot be instantiated directly.
3. A class uses `implements` to implement an interface.
4. A class must implement all inherited abstract methods unless the class is declared `abstract`.
5. Interface abstract methods are implicitly `public abstract`.
6. Interface variables are implicitly `public static final` (constants).
7. Interfaces do not have constructors.
8. A class can implement multiple interfaces.
9. An interface can extend multiple interfaces.

### Example: Interface Constants

Variables declared in an interface are automatically constants.

```java
interface Vehicle {

    int MAX_SPEED = 120;
}

public class Main {

    public static void main(String[] args) {

        System.out.println(Vehicle.MAX_SPEED);
    }
}
```

**Output:**

```text
120
```

The following declarations are equivalent:

```java
int MAX_SPEED = 120;
```

```java
public static final int MAX_SPEED = 120;
```

Because interface variables are constants, their values cannot be changed after initialization.

---

## 4. Implementing Multiple Interfaces

One important advantage of interfaces is that a Java class can implement **multiple interfaces**.

Unlike classes, Java does not allow a class to extend multiple classes. However, it allows a class to implement multiple interfaces.

### Example: Smartphone

A smartphone can perform several functions, such as taking pictures and playing music.

We can represent these behaviors using separate interfaces.

```java
interface Camera {

    void takePicture();
}

interface MusicPlayer {

    void playMusic();
}

class Smartphone implements Camera, MusicPlayer {

    @Override
    public void takePicture() {
        System.out.println("Taking a picture.");
    }

    @Override
    public void playMusic() {
        System.out.println("Playing music.");
    }
}

public class Main {

    public static void main(String[] args) {

        Smartphone phone = new Smartphone();

        phone.takePicture();
        phone.playMusic();
    }
}
```

**Output:**

```text
Taking a picture.
Playing music.
```

### Explanation

| Code | Explanation |
|---|---|
| `interface Camera` | Defines camera behavior. |
| `interface MusicPlayer` | Defines music player behavior. |
| `implements Camera, MusicPlayer` | Allows the class to implement both interfaces. |
| `takePicture()` | Implements the camera method. |
| `playMusic()` | Implements the music player method. |

**Key Point:** A class can implement as many interfaces as needed, allowing it to support different behaviors.

---

## 5. Interface Inheritance

An interface can inherit from another interface using the `extends` keyword.

Unlike classes, an interface can extend multiple interfaces.

### Example

```java
interface Animal {

    void eat();
}

interface Pet extends Animal {

    void play();
}

class Dog implements Pet {

    @Override
    public void eat() {
        System.out.println("Dog is eating.");
    }

    @Override
    public void play() {
        System.out.println("Dog is playing.");
    }
}

public class Main {

    public static void main(String[] args) {

        Dog dog = new Dog();

        dog.eat();
        dog.play();
    }
}
```

**Output:**

```text
Dog is eating.
Dog is playing.
```

### Explanation

- `Animal` defines the `eat()` method.
- `Pet` extends `Animal` and adds the `play()` method.
- `Dog` implements `Pet`.
- Because `Pet` inherits from `Animal`, `Dog` must implement both methods.

**Important:** A class that implements a child interface must implement all inherited abstract methods unless it is declared `abstract`.

---

## 6. Interfaces and Polymorphism

Interfaces can also be used to achieve runtime polymorphism.

An interface reference can refer to any object whose class implements that interface.

### Example: Payment System

```java
interface Payment {

    void pay(double amount);
}

class CreditCard implements Payment {

    @Override
    public void pay(double amount) {
        System.out.println("Paid $" + amount + " using Credit Card.");
    }
}

class PayPal implements Payment {

    @Override
    public void pay(double amount) {
        System.out.println("Paid $" + amount + " using PayPal.");
    }
}

public class Main {

    public static void main(String[] args) {

        Payment payment1 = new CreditCard();
        Payment payment2 = new PayPal();

        payment1.pay(100.00);
        payment2.pay(50.00);
    }
}
```

**Output:**

```text
Paid $100.0 using Credit Card.
Paid $50.0 using PayPal.
```

### Explanation

- `Payment` defines a common method called `pay()`.
- `CreditCard` and `PayPal` implement the interface differently.
- Both objects can be referenced using the `Payment` type.
- Java executes the appropriate overridden method at runtime.

**Key Idea:** Interfaces support polymorphism by allowing different classes to be used through the same interface reference.

---

## 7. Default and Static Methods in Interfaces

Modern Java interfaces can contain more than abstract methods.

They can also include `default` and `static` methods.

### Default Methods

A `default` method has a body and provides a default implementation that implementing classes can inherit or override.

```java
interface Animal {

    void makeSound();

    default void sleep() {
        System.out.println("Animal is sleeping.");
    }
}

class Dog implements Animal {

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

### Static Methods

A `static` method belongs to the interface itself and is called using the interface name.

```java
interface Calculator {

    static int add(int a, int b) {
        return a + b;
    }
}

public class Main {

    public static void main(String[] args) {

        int result = Calculator.add(10, 5);

        System.out.println("Result: " + result);
    }
}
```

**Output:**

```text
Result: 15
```

**Note:** Default and static methods are useful features of modern Java interfaces. Private helper methods are also supported in interfaces starting with Java 9.

---

## 8. Abstract Classes vs. Interfaces

Both abstract classes and interfaces support abstraction, but they serve different purposes.

| Feature | Abstract Class | Interface |
|---|---|---|
| Declaration | `abstract class` | `interface` |
| Inheritance Keyword | `extends` | `implements` (for classes) |
| Multiple Inheritance | A class can extend only one class | A class can implement multiple interfaces |
| Variables | Can have instance variables | Variables are constants (`public static final`) |
| Constructors | Can have constructors | Cannot have constructors |
| Abstract Methods | Can contain abstract methods | Can contain abstract methods |
| Implemented Methods | Can contain regular methods | Can contain `default` and `static` methods |
| Purpose | Share common state and behavior | Define a contract for classes |

### When Should You Use Each?

**Use an abstract class when:**
- Related classes share common fields and methods.
- You need constructors to initialize shared data.
- You want to provide common functionality to subclasses.

**Use an interface when:**
- Different classes need to follow the same contract.
- Classes need to support multiple behaviors.
- You want unrelated classes to share common functionality requirements.

---

## 9. Quick Review

**1. What is an interface in Java?**

<details>
<summary>Show Answer</summary>

An interface is a blueprint that defines methods a class agrees to implement.

</details>

**2. Which keyword is used to declare an interface?**

<details>
<summary>Show Answer</summary>

The `interface` keyword.

</details>

**3. Which keyword does a class use to implement an interface?**

<details>
<summary>Show Answer</summary>

The `implements` keyword.

</details>

**4. Can an interface be instantiated directly?**

<details>
<summary>Show Answer</summary>

No. An interface cannot be instantiated directly. A class must implement it before its objects can be created.

</details>

**5. Can a class implement multiple interfaces?**

<details>
<summary>Show Answer</summary>

Yes. A Java class can implement multiple interfaces.

Example:

```java
class Smartphone implements Camera, MusicPlayer {
}
```

</details>

**6. Can an interface extend another interface?**

<details>
<summary>Show Answer</summary>

Yes. An interface can extend one or multiple interfaces using the `extends` keyword.

</details>

**7. What happens if a class does not implement all inherited abstract methods?**

<details>
<summary>Show Answer</summary>

The class must be declared `abstract`. Otherwise, Java reports a compilation error.

</details>

**8. What is the difference between an abstract class and an interface?**

<details>
<summary>Show Answer</summary>

An abstract class can contain instance variables, constructors, and implemented methods. An interface defines a contract and supports multiple interface implementation by a class.

</details>

**9. Can interfaces contain methods with implementations?**

<details>
<summary>Show Answer</summary>

Yes. Interfaces can contain `default` and `static` methods with implementations. They can also contain private helper methods.

</details>

**10. How do interfaces support polymorphism?**

<details>
<summary>Show Answer</summary>

An interface reference can refer to objects of different classes that implement the same interface. Each class can provide its own implementation of the interface methods.

</details>

---
- [Oracle Java Tutorials – Implementing an Interface](https://docs.oracle.com/javase/tutorial/java/IandI/usinginterface.html)

