# 1. Getting Started with Java in IntelliJ IDEA

## 1.1 Prerequisites
Before writing Java code, ensure you have the following installed and configured:
* **IntelliJ IDEA** ([Community / Ultimate](https://www.jetbrains.com/idea/download/))
* **Java Development Kit (JDK)** ([Amazon Corretto 25](https://docs.aws.amazon.com/corretto/latest/corretto-25-ug/downloads-list.html))

---

## 1.2 Quickstart: First Java Class in IntelliJ

1. **Create Project:** Open IntelliJ -> **New Project** -> Name: `HelloWorld` -> Language: **Java** -> Build system: **IntelliJ** -> JDK: Select **Corretto-25** -> **Create**.

2. **Create Class:** Right-click `src` -> **New** -> **Java Class** -> Name: `HelloWorld`.

3. **Add Code:**

   ```java
   public class HelloWorld {
       public static void main(String[] args) {
           System.out.println("Hello World");
       }
   }
   ```

4. **Run the Program:** Click the green **Run** icon next to `main`, or right-click inside the `main` method and select **Run 'HelloWorld.main()'**.

   **Expected output:**

   ```text
   Hello World
   ```

---

### Understanding the Code

| Code                                     | Meaning                                      |
| ---------------------------------------- | -------------------------------------------- |
| `public class HelloWorld`                | Defines a class named HelloWorld (must match the .java filename).          |
| `public static void main(String[] args)` | The entry point of the program.              |
| `System.out.println("Hello World");`     | Prints text to the console.                  |
| `{ }`                                    | Marks the beginning and end of a code block. |
| `;`                                      | Marks the end of a Java statement.           |

---

## Executing Source Files Directly (No Manual `javac`)

Java allows you to run source files directly without manually compiling them first. The available features depend on the Java version.

| **Feature**                 | **Java Version** | **Command**                          | **Multi-File Support?**                        |
| --------------------------- | ---------------- | ------------------------------------ | ---------------------------------------------- |
| **Traditional Compilation** | Before Java 11   | `javac Hello.java` then `java Hello` | Manual compilation required                    |
| **Single-File Source**      | Java 11+         | `java Hello.java`                    | Single source file only                      |
| **Multi-File Source**       | Java 22+         | `java Hello.java`                    | Automatically compiles required source files |


## Java 25: Compact Source Files

Java 25 supports compact source files, letting beginners write simple programs with less boilerplate.

### Traditional Java

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

### Compact Source File (Java 25)

```java
void main() {
    IO.println("Hello World");
}
```
**Note:** In our class we will use the traditional version to understand Java classes and methods rather than trying compact source files.
---
## 1.3 Compiler Theory: How Java Works Under the Hood

Java uses a two-step execution model: **compilation** and **JVM execution**.

```text
+--------------------+       javac       +--------------------+       JVM       +----------------------+
|   Java Source Code |  -------------->  |    Java Bytecode   |  ------------> | Native Machine Code |
|   HelloWorld.java  |    Compilation    |   HelloWorld.class |    Execution    |     Hardware / OS    |
+--------------------+                   +--------------------+                 +----------------------+
```

1. **Compilation:** `javac` converts `.java` source code into `.class` bytecode.
2. **Execution:** The JVM executes the bytecode and may use **JIT compilation** to convert frequently executed code into native machine code.
3. **Portability:** The same bytecode can run on different operating systems with a compatible JVM.
4. **Error Detection:** The compiler catches many errors before the program runs.
---

## 1.4 Transitioning from Python to Java

| **Concept**                 | **Python**                     | **Java**                                                                           |
| --------------------------- | ------------------------------ | ---------------------------------------------------------------------------------- |
| **Typing**                  | Dynamic                        | Static                                                                             |
| **Print Output**            | `print("Hello")`               | `System.out.println("Hello");`                                                     |
| **Input / Console Reading** | `name = input("Enter name: ")` | `Scanner scanner = new Scanner(System.in);`<br>`String name = scanner.nextLine();` |
| **Code Blocks**             | Indentation                    | `{ }` curly braces                                                                 |
| **Statement Ending**        | New line                       | Semicolon `;` required                                                             |
| **Comments**                | `# Comment`                    | `// Comment`                                                                       |
| **Characters**              | `"a"` (String)                 | `'a'` (`char`)                                                                     |
| **Strings**                 | `"a"` (String)                 | `"a"` (`String`)                                                                   |
| **Boolean**                 | `True` / `False` | `true` / `false`      |

### Side-by-Side Example

**Python**

```python
name = "Alex"
age = 20

if age >= 18:
    print(f"{name} is an adult.")
```

**Java**

```java
public class Comparison {
    public static void main(String[] args) {
        String name = "Alex";
        int age = 20;

        if (age >= 18) {
            System.out.println(name + " is an adult.");
        }
    }
}
```

---
# 2. Variables & Primitive Data Types
In this section, you will learn how to store, manipulate, and work with data in memory using variables and Java's built-in primitive data types.

---

## 2.1 What is a Variable?

A **variable** is a named container in memory used to store data. In Java, every variable must have a declared **data type**, a **name**, and optionally an initial **value**.

```java
// Syntax: dataType variableName = value;
int age = 20;
String name = "Alex";
```
You MUST store data that matches the declared variable type. Attempting to assign an incompatible type will trigger a compile-time error:
```java
// Invalid: Type mismatch error
int myInt = "hello"; // The IDE/compiler will not let you compile this code
```

## 2.2 Java Primitive Data Types

Java provides **8 primitive data types**, divided into four main categories.

| **Category**   | **Type**  | **Size**      | **Usage / Range**                                                     |
| -------------- | --------- | ------------- | --------------------------------------------------------------------- |
| **Integers**   | `byte`    | 1 byte        | Small integers (-128 to 127)                                          |
|                | `short`   | 2 bytes       | Integers (-32,768 to 32,767)                                          |
|                | `int`     | 4 bytes       | Standard integers; common default choice                              |
|                | `long`    | 8 bytes       | Large integers; use `L` suffix, e.g., `10000000000L`                  |
| **Decimals**   | `float`   | 4 bytes       | Single-precision floating-point numbers; use `f` suffix               |
|                | `double`  | 8 bytes       | Double-precision floating-point numbers; default for decimal literals |
| **Characters** | `char`    | 2 bytes       | A single UTF-16 code unit, e.g., `'A'`                                |
| **Booleans**   | `boolean` | JVM-dependent | Logical values: `true` or `false`                                     |

---

## 2.3 Basic Code Example

The following example demonstrates how to declare primitive variables and print their values.

```java
public class VariablesDemo {
    public static void main(String[] args) {
        // Integer types
        int studentCount = 35;
        long population = 8_000_000_000L;

        // Decimal types
        double gpa = 3.85;
        float price = 19.99f;

        // Character and Boolean
        char grade = 'A';
        boolean isPassed = true;

        // Output values
        System.out.println("Student Count: " + studentCount);
        System.out.println("Population: " + population);
        System.out.println("GPA: " + gpa);
        System.out.println("Price: " + price);
        System.out.println("Grade: " + grade);
        System.out.println("Passed Course? " + isPassed);
    }
}
```

**Expected output:**

```text
Student Count: 35
Population: 8000000000
GPA: 3.85
Price: 19.99
Grade: A
Passed Course? true
```

---

## 2.4 Modern Java: Type Inference (`var`)

Starting with **Java 10**, the `var` keyword allows the compiler to infer a local variable's type from its initializer.

```java
public class VarDemo {
    public static void main(String[] args) {
        var score = 95;          // Inferred as int
        var message = "Success"; // Inferred as String
        var rating = 4.8;        // Inferred as double

        System.out.println(score);
        System.out.println(message);
        System.out.println(rating);
    }
}
```

**Key points:**

* `var` is available starting in Java 10.
* The variable must have an initializer so the compiler can infer its type.
* `var` does not make Java dynamically typed. The inferred type remains fixed.
* `var` can be used for local variables, including variables declared inside methods and loop variables.
* `var` cannot be used for fields, method parameters, or return types.

---

## 2.5 Naming Conventions and Rules

Follow these rules when naming Java variables:

* **CamelCase:** Start with a lowercase letter and capitalize subsequent words. Examples: `userScore`, `totalAmount`.
* **Valid characters:** Names can contain letters, digits, underscores (`_`), and dollar signs (`$`).
* **Cannot start with a digit:** `1stPlace` is invalid; `firstPlace` is valid.
* **Reserved keywords:** Java keywords such as `class`, `public`, `int`, and `static` cannot be used as variable names.
* **Case-sensitive:** `score`, `Score`, and `SCORE` are different identifiers.
* **Meaningful names:** Prefer `studentCount` over unclear names such as `x`.

**Summary:** Primitive types store basic values, `var` reduces repetitive type declarations, and meaningful variable names make Java code easier to read and maintain.

---

# 3. Operators & Arithmetic Expressions
In this section, you will learn how to perform calculations, compare values, and work with conditions using Java operators.

---

## 3.1 Arithmetic Operators

Arithmetic operators perform mathematical calculations.

| **Operator** | **Name**       | **Example** | **Result** |
| ------------ | -------------- | ----------- | ---------: |
| `+`          | Addition       | `10 + 3`    |       `13` |
| `-`          | Subtraction    | `10 - 3`    |        `7` |
| `*`          | Multiplication | `10 * 3`    |       `30` |
| `/`          | Division       | `10 / 3`    |        `3` |
| `%`          | Remainder      | `10 % 3`    |        `1` |

When both values are integers, `/` performs **integer division**.

| **Example** | **Result** |
| ----------- | ---------: |
| `5 / 2`     |        `2` |
| `5.0 / 2`   |      `2.5` |

---

## 3.2 Assignment Operators

Assignment operators assign or update values.

| **Operator** | **Example** | **Equivalent** | **Result** |
| ------------ | ----------- | -------------- | ---------: |
| `=`          | `x = 10`    | —              |       `10` |
| `+=`         | `x += 5`    | `x = x + 5`    |       `15` |
| `-=`         | `x -= 5`    | `x = x - 5`    |        `5` |
| `*=`         | `x *= 5`    | `x = x * 5`    |       `50` |
| `/=`         | `x /= 5`    | `x = x / 5`    |        `2` |
| `%=`         | `x %= 3`    | `x = x % 3`    |        `1` |

Assume `x = 10` before each example.

---

## 3.3 Comparison Operators

Comparison operators compare values and return `true` or `false`.

| **Operator** | **Meaning**              | **Example** | **Result** |
| ------------ | ------------------------ | ----------- | ---------- |
| `==`         | Equal to                 | `10 == 10`  | `true`     |
| `!=`         | Not equal to             | `10 != 5`   | `true`     |
| `>`          | Greater than             | `10 > 5`    | `true`     |
| `<`          | Less than                | `10 < 5`    | `false`    |
| `>=`         | Greater than or equal to | `10 >= 10`  | `true`     |
| `<=`         | Less than or equal to    | `10 <= 5`   | `false`    |

Remember:

| **Operator** | **Meaning** |
| ------------ | ----------- |
| `=`          | Assignment  |
| `==`         | Comparison  |

---

## 3.4 Logical Operators

Logical operators combine conditions.

| Operator | Meaning | Example | Result |
| :--- | :--- | :--- | :--- |
| `&&` | AND | `true && true` | `true` |
| `&&` | AND | `true && false` | `false` |
| `\|\|` | OR | `true \|\| false` | `true` |
| `\|\|` | OR | `false \|\| false` | `false` |
| `!` | NOT | `!true` | `false` |
| `!` | NOT | `!false` | `true` |
---

## 3.5 Increment and Decrement

`++` increases a value by `1`.

`--` decreases a value by `1`.

| **Operator** | **Example** | **Result** |
| ------------ | ----------- | ---------: |
| `++`         | `x++`       |    `x + 1` |
| `--`         | `x--`       |    `x - 1` |

### Prefix vs Postfix

| **Expression** | **Description**          | **Example**      |       **Result** |
| -------------- | ------------------------ | ---------------- | ---------------: |
| `x++`          | Use first, then increase | `x = 5; y = x++` | `y = 5`, `x = 6` |
| `++x`          | Increase first, then use | `x = 5; y = ++x` | `y = 6`, `x = 6` |

---

## 3.6 Ternary Operator

The ternary operator is a short way to choose between two values.

### Syntax

```text
condition ? valueIfTrue : valueIfFalse
```

| **Example**                    | **Result** |
| ------------------------------ | ---------- |
| `20 >= 18 ? "Adult" : "Minor"` | `"Adult"`  |
| `15 >= 18 ? "Adult" : "Minor"` | `"Minor"`  |

---

## 3.7 Operator Precedence

Java evaluates operators in a specific order.

For example:

| **Example**    | **Result** |
| -------------- | ---------: |
| `10 + 5 * 2`   |       `20` |
| `(10 + 5) * 2` |       `30` |

A simplified precedence order is:

```text
()
* / %
+ -
< > <= >=
== !=
&&
||
?:
= += -= *= /=
```

*** Use parentheses when you want to clearly control the order of operations.

---
## Next Steps

* [Java Tutorials](https://dev.java/learn/)
* [Java Language Basics](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)


---

**Happy coding!**

Output not appearing: Check the Run console for compilation errors.
Wrong Java version: Open File → Project Structure → Project and verify the Project SDK.
