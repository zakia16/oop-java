
# Module: Encapsulation and ArrayList

This module covers two important concepts in Java:

- **Encapsulation:** Protecting data by controlling access to an object's fields and methods.
- **ArrayList:** Managing collections of objects using Java's built-in `ArrayList` class.

---

## 1. Basic Principles of OOP

Object-Oriented Programming (OOP) is based on four fundamental principles:

| Principle | Description |
|:---|:---|
| **Encapsulation** | Bundles data and methods together and controls access to data. |
| **Abstraction** | Hides implementation details and exposes essential functionality. |
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

## 2. Encapsulation

**Encapsulation** combines data (fields) and the methods that operate on that data within a single unit called a **class**. It also restricts direct access to an object's data.

**Real-world example: Bank Account**

A bank account protects its balance from direct modification. Instead, users interact with it through methods such as `deposit()` and `withdraw()`.

<p align="center">
  <img src="https://github.com/user-attachments/assets/02273f56-c939-4417-96d2-3592b3556cdc"
       width="700"
       alt="Real-world example illustrating encapsulation">
</p>

<p align="center">
  <sub>
    Image source:
    <a href="https://takeuforward.org/blogs/oops/what-is-oops">TakeUForward – What is OOPs?</a>
  </sub>
</p>

### Key Idea

Make fields `private` and provide controlled access through `public` methods.

### Review Questions

**1. How is encapsulation implemented in Java?**

<details>
<summary>Show Answer</summary>

By declaring fields `private` and providing `public` getter and setter methods when appropriate.

</details>

**2. What are the benefits of encapsulation?**

<details>
<summary>Show Answer</summary>

- **Security:** Prevents unauthorized direct access to data.
- **Control:** Allows validation before changing data.
- **Flexibility:** Internal implementation can change without affecting how other classes use it.

</details>

---


Code Example

Here is a practical example showing how a BankAccount class protects its balance variable from invalid updates:

```java
public class BankAccount {
    // 1. Private variable hidden from outside classes
    private double balance;

    // 2. Public getter method for read access
    public double getBalance() {
        return balance;
    }

    // 3. Public setter/action method with validation logic
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        } else {
            System.out.println("Deposit amount must be positive.");
        }
    }
}
```
In this example, external code cannot run account.balance = -500; because balance is private. Instead, any change must pass through deposit(), which validates the input first.

