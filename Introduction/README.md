# 1. Getting Started with Java in IntelliJ IDEA

## Prerequisites

* **IntelliJ IDEA** ([Community / Ultimate](https://www.jetbrains.com/idea/download/))
* **Java Development Kit (JDK)** ([Amazon Corretto 25](https://docs.aws.amazon.com/corretto/latest/corretto-25-ug/downloads-list.html))

---

## Quickstart: First Java Class in IntelliJ

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

## Understanding the Code

| Code                                     | Meaning                                      |
| ---------------------------------------- | -------------------------------------------- |
| `public class HelloWorld`                | Defines a class named `HelloWorld`.          |
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

Java 25 supports compact source files, allowing beginners to write simple programs with less boilerplate code.

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

**Key differences:**

* Traditional Java explicitly declares a class and a `main` method.
* Compact source files do not require an explicit class declaration.
* The compact form supports an instance `main` method.
* `IO.println()` is available through Java's `java.io.IO` API and is automatically imported in compact source files.

**Note:** Start with the traditional version to understand Java classes and methods before trying compact source files.

---

## Troubleshooting

* **JDK not found:** Verify that JDK 25 is installed and selected in the project settings.
* **Run icon missing:** Ensure the file is named `HelloWorld.java` and the class name matches the filename.
* **No output:** Check the Run console for compilation errors and confirm that you are running the correct class.
* **Wrong Java version:** Open **File -> Project Structure -> Project** and verify the Project SDK.

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
## Next Steps

* [Java Tutorials](https://dev.java/learn/)
* [Java Language Basics](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)


---

**Happy coding!**

Output not appearing: Check the Run console for compilation errors.
Wrong Java version: Open File → Project Structure → Project and verify the Project SDK.
