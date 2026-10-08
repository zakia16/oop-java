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

## 2. Loops and Control Statements

Loops execute a block of code repeatedly while a condition is satisfied or for a specified number of iterations.

### 2.1 `while` Loop

Executes repeatedly **while the condition is `true`**. Useful when the number of iterations is unknown.

**Syntax:**

```java
while (condition) {
    // Code to execute
}
```

**Example:**

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

**Key Point:** Update the loop variable to avoid an infinite loop.

### 2.2 `do-while` Loop

Executes the code block **at least once** before checking the condition.

**Syntax:**

```java
do {
    // Code to execute
} while (condition);
```

**Example:**

```java
int n = 6;

do {
    System.out.println(n);
    n++;
} while (n < 10);
```

**Key Point:** The condition is checked after each iteration. Notice the semicolon (`;`) after `while (condition)`.

### 2.3 `for` Loop

Repeats a block of code using initialization, a condition, and an update expression.

**Syntax:**

```java
for (initialization; condition; update) {
    // Code to execute
}
```

**Example:**

```java
for (int i = 1; i <= 10; i++) {
    System.out.println("9 x " + i + " = " + (9 * i));
}
```

**Key Points:**

* **Initialization:** Runs once at the beginning.
* **Condition:** Checked before each iteration.
* **Update:** Runs after each iteration.

### 2.4 Nested `for` Loops

A nested loop is a loop inside another loop. The inner loop completes each iteration before the outer loop advances.

**Example:**

```java
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

**Output:**

```text
*
**
***
****
*****
```

**Key Point:** Nested loops are useful for patterns, tables, and multidimensional arrays.

### 2.5 `break` Statement

The `break` statement immediately terminates the innermost loop.

**Example:**

```java
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break;
    }
    System.out.print(i + " ");
}
```

**Output:**

```text
0 1 2 3 4
```

### 2.6 `continue` Statement

The `continue` statement skips the remaining code in the current iteration and proceeds to the next iteration.

**Example:**

```java
for (int i = 0; i < 5; i++) {
    if (i == 2) {
        continue;
    }
    System.out.print(i + " ");
}
```

**Output:**

```text
0 1 3 4
```

### 2.7 Summary

| Statement    | Purpose                                              |
| ------------ | ---------------------------------------------------- |
| `while`      | Repeats while a condition is `true`.                 |
| `do-while`   | Executes at least once, then checks the condition.   |
| `for`        | Repeats using initialization, condition, and update. |
| Nested loops | Places one loop inside another.                      |
| `break`      | Terminates the innermost loop.                       |
| `continue`   | Skips the current iteration.                         |
---

## 3. Java Strings & Text Processing

A **`String`** is an object that represents a sequence of characters. String literals are enclosed in double quotes (`" "`).

## 3.1 `char` vs. `String`

* **`char`**: Stores a single character using single quotes (`' '`).
* **`String`**: Represents a sequence of characters using double quotes (`" "`).

```java
char grade = 'A';
String courseName = "CS 1336";
```

### String Indexing

String indexes start at `0`.

```java
String text = "Java";

System.out.println(text.charAt(0)); // J
System.out.println(text.charAt(3)); // a
```

For `"Java"`:

```text
 J   a   v   a
 0   1   2   3
```

---

## 3.2 String Concatenation

The `+` operator can be used to combine strings.

```java
String firstName = "John";
String lastName = "Smith";

String fullName = firstName + " " + lastName;

System.out.println(fullName); // John Smith
```

Strings can also be combined with other data types:

```java
int age = 20;

System.out.println("Age: " + age); // Age: 20
```

---

## 3.3 Essential String Methods

| **Method**              | **Return Type** | **Description**                                                       |
| ----------------------- | --------------- | --------------------------------------------------------------------- |
| `length()`              | `int`           | Returns the number of characters.                                     |
| `charAt(index)`         | `char`          | Returns the character at a zero-based index.                          |
| `substring(start, end)` | `String`        | Extracts characters from `start` to `end - 1`.                        |
| `toLowerCase()`         | `String`        | Converts to lowercase.                                                |
| `toUpperCase()`         | `String`        | Converts to uppercase.                                                |
| `trim()`                | `String`        | Removes leading and trailing whitespace.                              |
| `contains(str)`         | `boolean`       | Checks whether the string contains the specified text.                |
| `indexOf(str)`          | `int`           | Returns the index of the first occurrence; returns `-1` if not found. |
| `startsWith(str)`       | `boolean`       | Checks whether the string starts with the specified text.             |
| `endsWith(str)`         | `boolean`       | Checks whether the string ends with the specified text.               |
| `replace(old, new)`     | `String`        | Replaces occurrences of text.                                         |
| `toCharArray()`         | `char[]`        | Converts the string into a character array.                           |
| `isEmpty()`             | `boolean`       | Checks whether the string has zero characters.                        |
| `isBlank()`             | `boolean`       | Checks whether the string is empty or contains only whitespace.       |

**Example:**

```java
String text = "Hello Java";

System.out.println(text.length());                  // 10
System.out.println(text.charAt(0));                 // H
System.out.println(text.substring(0, 5));           // Hello
System.out.println(text.toUpperCase());             // HELLO JAVA
System.out.println(text.toLowerCase());             // hello java
System.out.println("  Hello  ".trim());             // Hello
System.out.println(text.contains("Java"));          // true
System.out.println(text.indexOf("Java"));           // 6
System.out.println(text.startsWith("Hello"));       // true
System.out.println(text.endsWith("Java"));          // true
System.out.println(text.replace("Java", "World"));  // Hello World
System.out.println(text.isEmpty());                 // false
```

---

## 3.4 String Equality: `.equals()` vs. `==`

Use `.equals()` to compare String contents. The `==` operator compares object references.

```java
String str1 = new String("Hello");
String str2 = new String("Hello");

System.out.println(str1 == str2);                   // false
System.out.println(str1.equals(str2));              // true
System.out.println(str1.equalsIgnoreCase("hello")); // true
```

* **`==`**: Checks whether references point to the same object.
* **`.equals()`**: Compares String contents, including case.
* **`.equalsIgnoreCase()`**: Compares String contents without considering case.

---

## 3.5 String Immutability

Strings are **immutable**, meaning their contents cannot be changed after creation. String methods return new strings rather than modifying the original.

```java
String text = "hello";

text.toUpperCase();

System.out.println(text); // hello

text = text.toUpperCase();

System.out.println(text); // HELLO
```

---

## 3.6 Character Operations

Java's `Character` class provides methods to check and convert individual characters.

| **Method**                  | **Description**                          | **Example**                  | **Result** |
| --------------------------- | ---------------------------------------- | ---------------------------- | ---------- |
| `Character.isLetter(ch)`    | Checks whether a character is a letter.  | `Character.isLetter('t')`    | `true`     |
| `Character.isDigit(ch)`     | Checks whether a character is a digit.   | `Character.isDigit('5')`     | `true`     |
| `Character.isUpperCase(ch)` | Checks whether a character is uppercase. | `Character.isUpperCase('T')` | `true`     |
| `Character.isLowerCase(ch)` | Checks whether a character is lowercase. | `Character.isLowerCase('t')` | `true`     |
| `Character.toUpperCase(ch)` | Converts to uppercase.                   | `Character.toUpperCase('t')` | `'T'`      |
| `Character.toLowerCase(ch)` | Converts to lowercase.                   | `Character.toLowerCase('T')` | `'t'`      |

**Example:**

```java
String str = "cit";

char firstChar = str.charAt(0);
char[] chars = str.toCharArray();

boolean isLetter = Character.isLetter('t'); // true
boolean isDigit = Character.isDigit('5');   // true

char upper = Character.toUpperCase('t');    // 'T'
char lower = Character.toLowerCase('T');    // 't'
```

### Comparing Characters

Characters can be compared using `==`, `<`, and `>` based on their Unicode values.

```java
char ch1 = 's';
char ch2 = 't';

System.out.println(ch1 == ch2); // false
System.out.println(ch1 < ch2);  // true
System.out.println(ch1 > ch2);  // false
```

## Key Point

Use **`char`** for individual characters, **`String`** for text, and the **`Character`** class for character checks and conversions.
---

## 4. Fixed-Size 1D Arrays

An **array** is a fixed-size container that stores elements of the same data type. Indexes range from `0` to `length - 1`.

### 4.1 Declaring and Initializing Arrays

```java
// Fixed length: elements receive default values
int[] scores = new int[5]; // indexes 0–4

// Array literal
int[] numbers = {10, 20, 30, 40, 50};
```

**Key Point:** An array's size is fixed after creation.

### 4.2 Accessing and Modifying Elements

```java
int[] ages = {18, 20, 22, 25};

System.out.println(ages[0]); // 18

ages[1] = 21;                // Modify element

System.out.println(ages.length); // 4
```

* Indexes start at `0`.
* Use `array[index]` to access or modify an element.
* Use `array.length` to get the number of elements.
* Valid indexes are `0` through `length - 1`.

```java
// ages[4] = 30; // Error: ArrayIndexOutOfBoundsException
```

### 4.3 Iterating Over Arrays

#### Standard `for` Loop

Use when you need the index.

```java
int[] values = {5, 10, 15, 20};

for (int i = 0; i < values.length; i++) {
    System.out.println("Index " + i + ": " + values[i]);
}
```

#### Enhanced `for-each` Loop

Use when you only need each element.

```java
String[] fruits = {"Apple", "Banana", "Cherry"};

for (String fruit : fruits) {
    System.out.println(fruit);
}
```

### 4.4 Array Default Values

When an array is created with `new`, its elements receive default values.

| Type                           | Default    |
| ------------------------------ | ---------- |
| `int`, `long`, `short`, `byte` | `0`        |
| `double`, `float`              | `0.0`      |
| `char`                         | `'\u0000'` |
| `boolean`                      | `false`    |
| Reference types                | `null`     |

```java
int[] numbers = new int[3];

System.out.println(numbers[0]); // 0
```

### 4.5 Common Array Operations

#### Sum

```java
int[] numbers = {10, 20, 30};
int sum = 0;

for (int number : numbers) {
    sum += number;
}

System.out.println(sum); // 60
```

#### Find Maximum

```java
int[] numbers = {10, 45, 20, 30};
int max = numbers[0];

for (int number : numbers) {
    if (number > max) {
        max = number;
    }
}

System.out.println(max); // 45
```

#### Search for a Value

```java
int[] numbers = {10, 20, 30, 40};
int target = 30;
boolean found = false;

for (int number : numbers) {
    if (number == target) {
        found = true;
        break;
    }
}

System.out.println(found); // true
```

## 5. Integrated Practical Code Example

This example combines **arrays, `Scanner`, loops, calculations, `printf()`, and `if-else`**.

```java
import java.util.Scanner;

public class Week2Demo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        double[] scores = new double[3];

        // Input scores
        for (int i = 0; i < scores.length; i++) {
            System.out.print("Enter score for Exam " + (i + 1) + ": ");
            scores[i] = scanner.nextDouble();
        }

        // Calculate average
        double sum = 0;

        for (double score : scores) {
            sum += score;
        }

        double average = sum / scores.length;

        System.out.printf("%nAverage Score: %.2f%n", average);

        // Evaluate result
        if (average >= 70.0) {
            System.out.println("Status: PASS");
        } else {
            System.out.println("Status: FAIL");
        }

        scanner.close();
    }
}
```
---
