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

   Run: Click the green Run icon next to main (or right-click inside main → Run 'HelloWorld.main()').Executing Source Files Directly (No Manual javac)FeatureJava VersionCommandMulti-File Support?TraditionalPrior to Java 11javac Hello.java then java HelloManual compilation requiredSingle-File SourceJava 11+java Hello.java❌ Single file onlyMulti-File SourceJava 22+java Hello.java✅ Auto-detects dependenciesModern Java 25: Compact Source Files & Instance MainJava 25 reduces boilerplate for quick scripts, demos, and beginners by removing required class wrappers and static keywords.Before vs. AfterJava// Traditional
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
Java// Java 25 Compact Source File
void main() {
    IO.println("Hello World!");
}
Key ChangesImplicit Class: Top-level class declarations are optional; the compiler generates one automatically.Instance main Methods: main() no longer needs to be static. Valid signatures include void main(), public void main(), and traditional String[] args variants (JVM prefers main(String[] args) if both exist).
