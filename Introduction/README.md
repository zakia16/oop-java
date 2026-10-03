# Getting Started with Java in IntelliJ IDEA

## Prerequisites
* **IntelliJ IDEA** ([Community / Ultimate](https://www.jetbrains.com/idea/download/))
* **Java Development Kit (JDK)** ([Amazon Corretto 25](https://docs.aws.amazon.com/corretto/latest/corretto-25-ug/downloads-list.html))

---

## Quickstart: First Java Class in IntelliJ

1. **Create Project:** Open IntelliJ &rarr; **New Project** &rarr; Name: `HelloWorld` &rarr; Language: **Java** &rarr; Build system: **IntelliJ** &rarr; JDK: Select **Corretto-25** &rarr; **Create**.
2. **Create Class:** Right-click `src` &rarr; **New** &rarr; **Java Class** &rarr; Name: `HelloWorld`.
3. **Add Code:**
   ```java
   public class HelloWorld {
       public static void main(String[] args) {
           System.out.println("Hello World");
       }
   }
   ```

4. Run: Click the green Run icon next to main (or right-click inside main -> Run 'HelloWorld.main()').

Expected output:

Hello World!
Understanding the Code
Code	Meaning
public class HelloWorld	Defines a class named HelloWorld.
public static void main(String[] args)	Defines the program's entry point.
System.out.println("Hello World!");	Prints text to the console.
{ }	Marks the beginning and end of a code block.
;	Marks the end of a Java statement.
Java 25: Traditional vs. Compact Source Files

Java 25 supports compact source files, which let beginners write simple programs with less boilerplate.

Traditional Java:

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}

Compact source file in Java 25:

void main() {
    IO.println("Hello World!");
}

The compact example uses Java 25's implicitly declared class and instance main method features. IO.println() is available through the java.io.IO API, which is automatically imported in compact source files.

Note: Use the traditional version for this IntelliJ quickstart. It introduces the standard class and main method structure commonly used in Java projects.

Troubleshooting
JDK not found: Verify that JDK 25 is installed and selected in the project settings.
Run icon missing: Make sure the code is saved in HelloWorld.java and the class name matches the filename.
Output not appearing: Check the Run console for compilation errors.
Wrong Java version: Open File → Project Structure → Project and verify the Project SDK.
