
# Module: Encapsulation

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


## 2. Encapsulation

**Encapsulation** combines data (fields) and the methods that operate on that data into a single unit called a class. It also restricts direct access to an object's data.

<img width="396" height="231" alt="image" src="https://github.com/user-attachments/assets/cbb30c75-e138-4a63-a8a2-4e47cf48ff14" />

### Key Components of Encapsulation

Encapsulation in Java is achieved using two main components:

1. **Private Fields (`private`)**
   - Instance variables are declared `private` to restrict direct access from outside the class.
   - This protects an object's data from unintended changes.

2. **Public Methods (`public`)**
   - **Getter methods** allow access to private fields.
   - **Setter methods** allow controlled modification of private fields.
   - Setters can also validate values before updating fields.

**Example:**

```java
public class Student {
    private String name;  // Private field

    // Getter
    public String getName() {
        return name;
    }

    // Setter
    public void setName(String name) {
        this.name = name;
    }
}
```

> **Key Idea:** Keep data private and provide controlled access through public methods.


### Real-world example: Bank Account**

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


### Code Example: BankAccount

The following example demonstrates how encapsulation protects a bank account's balance from unauthorized or invalid changes.

```java
public class BankAccount {

    // Private field: Direct access is restricted
    private double balance;

    // Constructor
    public BankAccount(double initialBalance) {
        if (initialBalance >= 0) {
            this.balance = initialBalance;
        }
    }

    // Deposit money
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount);
        } else {
            System.out.println("Deposit amount must be positive.");
        }
    }

    // Withdraw money
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrew: $" + amount);
        } else {
            System.out.println("Invalid withdrawal amount or insufficient funds.");
        }
    }

    // Getter: Read the current balance
    public double getBalance() {
        return balance;
    }
}
```

### Using the BankAccount Class

```java
public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(100.0);

        // ❌ Direct access blocked (causes a compile error)
        // account.balance = 100000000.0;     

        // ✅ Safe access through public methods
        account.deposit(50.0);   // Valid: balance becomes 150.0
        account.withdraw(30.0);  // Valid: balance becomes 120.0
        account.withdraw(500.0); // Blocked by method validation
    }
}
```

### Understanding the Example

| Component | Purpose |
|:---|:---|
| `private double balance` | Protects the account balance from direct access. |
| `getBalance()` | Getter: Allows reading the balance. |
| `deposit()` | Allows adding money with validation. |
| `withdraw()` | Allows withdrawing money with validation. |

> **Important:** A setter is not always necessary. Methods such as `deposit()` and `withdraw()` can provide controlled ways to modify private fields without allowing unrestricted changes.


## Benefits of Encapsulation

| Benefit | Explanation |
|---|---|
| Data Protection | Prevents direct access to an object's internal data. |
| Controlled Access | Allows data to be modified through methods that can validate input. |
| Data Integrity | Helps prevent invalid values and keeps an object's data consistent. |
| Flexibility | Internal implementation can change without requiring changes to other classes that use the object. |
| Maintainability | Makes programs easier to understand, test, and update. |

---

### Review Questions


## 5. Quick Review

**1. What is encapsulation?**

<details>
<summary>Show Answer</summary>

Encapsulation combines data and methods inside a class while restricting direct access to the data.

</details>

**2. How is encapsulation implemented in Java?**

<details>
<summary>Show Answer</summary>

By declaring fields `private` and providing `public` getter and setter methods when appropriate.

</details>

**3. What is the purpose of a getter method?**

<details>
<summary>Show Answer</summary>

A getter method returns the value of a private field.

</details>

**4. What is the purpose of a setter method?**

<details>
<summary>Show Answer</summary>

A setter method modifies the value of a private field. It can also validate the new value before changing it.

</details>

**5. Does every private field need a getter and setter?**

<details>
<summary>Show Answer</summary>

No. Provide getters and setters only when needed. Some fields should not be directly modified after an object is created.

</details>

**6. Why is encapsulation important?**

<details>
<summary>Show Answer</summary>

It protects data, controls how objects are modified, and helps maintain data integrity.

</details>

