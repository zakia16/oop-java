
# Module: Encapsulation

In our previous modules, we learned how to build classes, instantiate objects, and write instance methods. However, in those initial examples, our fields were wide open, which means any external code could modify an object's data directly (like setting a negative balance or an invalid GPA).

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

## 3. Encapsulation

**Encapsulation** combines data (fields) and the methods that operate on that data into a single unit called a class. It also restricts direct access to an object's data.

<img width="396" height="231" alt="image" src="https://github.com/user-attachments/assets/cbb30c75-e138-4a63-a8a2-4e47cf48ff14" />

### Example of Basic Encapsulation:
Imagine we are writing a program to manage a bank account. We need a variable to store the account balance and a method to deposit money.
Without using a class, we might write:

```java
public class Main {
    public static void main(String[] args) {
        double balance = 1000;
        // Deposit money
        balance = balance + 500;
        System.out.println("Balance: $" + balance);
    }
}
```
Let's use a Class to Encapsulate Data and Methods:

BankAccount.java
```java
public class BankAccount {

    double balance;

    public BankAccount(double balance) {
      this.balance = balance;
    }
    // Deposit money
    public void deposit(double amount) {
        balance += amount;
    }

    // Display balance
    public void displayBalance() {
        System.out.println("Balance: $" + balance);
    }
}
```

### The Problem: Is our data still safe?

Now, suppose another programmer, Bob, writes code to update the account balance:

Main.java
```java
public class Main {
    public static void main(String[] args) {
      BankAccount account = new BankAccount(10000.0);
      account.balance = 10000000;   // Bob directly changes the account balance!
  }
}
```

#### What Went Wrong?

Imagine Bob looks at his friend's bank account and thinks:

*"Your balance is looking a little low. Let me fix that for you!"*

So, he changes the balance to **$10 million**! Suddenly, his friend is a millionaire without depositing a single dollar. Bob just created money out of thin air! 😂

**The problem:** Because `balance` has no access modifier, other classes in the same package can access it directly. Bob can directly change it without any validation, as long as his code is in the same package.

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
        BankAccount account = new BankAccount(10000.0);

        // ❌ Direct access blocked (causes a compile error)
        // account.balance = 100000000.0;

        // ✅ Safe access through public methods
        account.deposit(50.0);
        account.withdraw(30.0);
        account.withdraw(500.0);
    }
}
```
> **Important:** A setter is not always necessary. Methods such as `deposit()` and `withdraw()` can provide controlled ways to modify private fields without allowing unrestricted changes.

### Key Components of Encapsulation

In Java, encapsulation is commonly achieved by:

1. Declaring fields as `private`.
2. Providing `public` getter and setter methods when access is needed.

## 4. Getters and Setters

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

---

## 5. Controlling Access: Read-Only and Write-Only

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
Other classes can retrieve the balance but cannot change it through a `setter`.

### Write-Only Example

```java
public class Password {

    private String password;

    public void setPassword(String password) {
        this.password = password;
    }
}
```

No `getter` is provided because passwords are sensitive information. Other classes can set a password, but they should not be able to retrieve it directly. This helps protect sensitive data from unnecessary exposure.

---

## 6. Benefits of Encapsulation

- **Information Hiding:**: Encapsulation allows the internal representation of an object to be hidden from the outside. Only the necessary details are exposed through a public interface.
- **Data Integrity:** Methods can validate input and help prevent invalid values.
- **Increased Flexibility**: By controlling access to the fields of a class, you can change the internal implementation without affecting the external code using the class.
- **Improved Maintainability**: Encapsulation helps in maintaining the code by keeping the fields private and providing public getter and setter methods to modify and view the fields.
- 
---

## 7. Quick Review

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
