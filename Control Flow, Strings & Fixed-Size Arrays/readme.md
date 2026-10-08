In this module, you will learn to control program execution using conditional statements and loops, manipulate text with Java's `String` class, and store data using one-dimensional arrays.

---

## 1. Conditional Statements (Decision Making)

Conditional statements execute different blocks of code based on Boolean expressions (`true` or `false`).

### 1.1 The `if`, `else if`, and `else` Ladder

Evaluates conditions in order and executes the first matching block.

**Java Example:**

```java
int score = 85;

if (score >= 90) {
    System.out.println("Grade: A");
} else if (score >= 80) {
    System.out.println("Grade: B");
} else if (score >= 70) {
    System.out.println("Grade: C");
} else {
    System.out.println("Grade: F");
}
```

**Output:**

```text
Grade: B
```

**Key Points:**

* `if`: Checks the first condition.
* `else if`: Checks additional conditions.
* `else`: Executes if all previous conditions are false.

### 1.2 Switch Statements and Expressions

Java supports traditional `switch` statements and modern arrow syntax (`->`).

**Traditional `switch`:**

```java
int day = 3;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    default:
        System.out.println("Invalid day");
}
```

**Modern `switch` Expression (Java 14+):**

```java
int day = 3;

String dayName = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    default -> "Invalid day";
};

System.out.println(dayName);
```

**Key Points:**

* `case` defines possible matching values.
* `break` prevents fall-through in traditional `switch` statements.
* `default` handles unmatched values.
* Arrow syntax (`->`) eliminates fall-through and does not require `break`.
* Switch expressions return values that can be assigned to variables.

---
