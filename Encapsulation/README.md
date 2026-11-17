
# Module: Encapsulation

In our previous modules, we learned how to build classes, instantiate objects, and write instance methods. However, in those initial examples, our fields were wide open which means any external code could modify an object's data directly (like setting a negative balance or an invalid GPA).

In professional software development, leaving object data unprotected is a recipe for bugs and security issues. To build secure, maintainable, and scalable applications, we need strict rules for data visibility.

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

## 2. Access Modifiers in Java

Before learning how to implement encapsulation, we need to understand **access modifiers**.

Access modifiers control the visibility and accessibility of class members, such as fields, methods, and constructors.

Java provides four access levels:

| Access Modifier | Accessibility |
|:---|:---|
| `public` | Accessible from any class. |
| `private` | Accessible only within the class where it is declared. |
| `protected` | Accessible within the same package and by subclasses in other packages through inheritance. |
| `default` (no modifier) | Accessible only within the same package (package-private). |

### Example: Access Modifiers

```java
public class MyClass {
    public int publicField;         // Accessible from any class
    private int privateField;       // Accessible only within MyClass
    protected int protectedField;   // Same package and subclasses
    int defaultField;               // Same package only
}
```
**Key Point:** Use `private` to protect data and `public` to provide controlled access through methods.

## 2. Encapsulation

**Encapsulation** combines data (fields) and the methods that operate on that data into a single unit called a class. It also restricts direct access to an object's data.

<img width="396" height="231" alt="image" src="https://github.com/user-attachments/assets/cbb30c75-e138-4a63-a8a2-4e47cf48ff14" />


## 1. The Problem: Why Do We Need Encapsulation?

To understand why this matters, imagine we created a `BankAccount` class to manage a customer's bank balance.

```java
public class BankAccount {
    double balance;
}
```

Now, suppose another programmer, Bob, writes code to update the account balance:

```java
public void updateAccount(BankAccount account) {
    account.balance = 10000000;
    // More banking code
}
```

### What Went Wrong?

Imagine Bob looks at his friend's bank account and thinks:

*"Your balance is looking a little low. Let me fix that for you!"*

So, he changes the balance to **$10 million**! Suddenly, his friend is a millionaire without depositing a single dollar. Bob just created money out of thin air! 😂

**The problem:** Because balance has no access modifier, other classes in the same package can access it directly. Bob can directly change it without any validation, as long as his code is in the same package.

To prevent this problem, we need encapsulation!

### How Do We Implement Encapsulation?

We make the `balance` field `private` so other classes cannot access it directly. Instead, we provide `public` methods to control how the data is accessed or modified.

For example, a bank account can provide methods such as `deposit()` and `withdraw()` rather than allowing other classes to change the balance directly.

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

```java
public class BankAccount {

    private double balance;

    public void setBalance(double amount) {
        if (amount >= 0) {
            balance = amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

This gives us several important benefits:

1. **Validation Control:** The class controls what values can be stored. For example, the setter rejects negative balances.
2. **Read-Only / Write-Only Access:** Fields can be made read-only or write-only by omitting the setter or getter.
3. **Implementation Independence:** Other classes do not need to know how the class stores its data internally. We can change the internal implementation without requiring changes to the code that uses the class.


### Key Components of Encapsulation

In Java, encapsulation is commonly achieved by:

1. Declaring fields as `private`.
2. Providing `public` getter and setter methods when access is needed.

### Example

```java
public class Student {

    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

In this example:

- `name` and `age` are private fields.
- Other classes cannot access these fields directly.
- The `getName()` method provides controlled access to the name.
- The `setName()` method allows the name to be modified.

### Key Idea

Encapsulation protects an object's internal data and controls how other classes access or modify it.

---

## 2. Getters and Setters

Getters and setters are methods commonly used to access and modify private fields.

### Getter

A **getter** returns the value of a private field.

```java
public String getName() {
    return name;
}
```

### Setter

A **setter** changes the value of a private field.

```java
public void setName(String name) {
    this.name = name;
}
```

### Complete Example

```java
public class Student {

    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        if (age >= 0) {
            this.age = age;
        }
    }

    public int getAge() {
        return age;
    }
}
```

**Main.java**

```java
public class Main {

    public static void main(String[] args) {

        Student student = new Student();

        student.setName("Alex");
        student.setAge(20);

        System.out.println(student.getName());
        System.out.println(student.getAge());
    }
}
```

**Output:**

```text
Alex
20
```

### Why Use Setters?

Setters allow a class to validate data before storing it.

For example:

```java
public void setAge(int age) {
    if (age >= 0) {
        this.age = age;
    }
}
```

This prevents a negative age from being stored through the setter.

### Why Use Getters?

Getters allow other classes to retrieve information without directly accessing private fields.

---

## 3. Controlling Access: Read-Only and Write-Only

One advantage of encapsulation is that a class can control how other classes access its fields.

You do not have to provide both a getter and a setter for every field.

| Access | How to Provide It |
|---|---|
| Read and Write | Provide both getter and setter. |
| Read-Only | Provide a getter but no setter. |
| Write-Only | Provide a setter but no getter. |
| No Public Access | Provide neither getter nor setter. |

### Read-Only Example

```java
public class Account {

    private double balance;

    public Account(double balance) {
        this.balance = balance;
    }

    public double getBalance() {
        return balance;
    }
}
```

Other classes can retrieve the balance but cannot change it through a setter.

### Write-Only Example

```java
public class Password {

    private String password;

    public void setPassword(String password) {
        this.password = password;
    }
}
```

Other classes can set the password but cannot retrieve it through a getter.

**Key Idea:** Provide only the methods that other classes need.

---

## 5. Benefits of Encapsulation

Encapsulation provides several benefits:

- Fields can be made read-only or write-only.
- A class has control over what is stored in its fields.
- Other classes do not need to know how data is stored internally.
- The internal implementation can change without requiring changes to calling code, provided the public interface remains compatible.
- It helps make code more flexible and maintainable.

---



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

