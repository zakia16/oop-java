# Getting Started with Java in IntelliJ IDEA

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

## Next Steps

* [Java Tutorials](https://dev.java/learn/)
* [Java Language Basics](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)


---

**Happy coding!**

Output not appearing: Check the Run console for compilation errors.
Wrong Java version: Open File → Project Structure → Project and verify the Project SDK.
