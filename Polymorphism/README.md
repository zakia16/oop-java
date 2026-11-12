
# Basic Principles of Object-Oriented Programming (OOP)

Object-Oriented Programming (OOP) is a programming approach organized around **objects**, which combine data and behavior.

OOP is built on four fundamental principles:

| Principle | Description |
|:---|:---|
| **Encapsulation** | Bundles data and methods together while controlling access to data. |
| **Abstraction** | Hides implementation details and exposes only essential functionality. |
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
---

## Polymorphism

**Polymorphism** means "many forms." It allows the same method or operation to behave differently depending on the object that uses it.

**Real-world example: Animal Sounds**

A method named `makeSound()` can produce different results depending on the animal:

- A `Dog` barks.
- A `Cat` meows.
- A `Bird` chirps.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e8a87f53-9595-456c-823e-406f260346fb"
       width="700"
       alt="Animal sounds illustrating polymorphism">
</p>

### Key Idea

The same method call can produce different behaviors for different objects.

### Review Questions

**1. Why is polymorphism useful?**

<details>
<summary>Show Answer</summary>

It makes code more flexible, reusable, and easier to extend.

</details>

**2. What are the two main types of polymorphism in Java?**

<details>
<summary>Show Answer</summary>

- **Compile-time polymorphism:** Achieved through method overloading.
- **Runtime polymorphism:** Achieved through method overriding.

</details>

**3. How does polymorphism support extensibility?**

<details>
<summary>Show Answer</summary>

New classes can provide their own implementations of methods without changing the code that uses the common parent class or interface.

</details>

---
