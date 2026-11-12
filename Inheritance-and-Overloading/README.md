
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
## Inheritance

**Inheritance** allows one class to acquire the properties (fields) and behaviors (methods) of another class. It promotes **code reuse** and helps establish relationships between classes.

**Real-world example: Vehicles**

A `Car` and a `Bike` can inherit common properties and methods from a parent class called `Vehicle`.

For example, both vehicles may share properties such as `color` and `speed`, and methods such as `start()` and `stop()`.

<p align="center">
  <img src="https://github.com/user-attachments/assets/4a843286-4361-41da-95bb-5d009fa0365e"
       width="700"
       alt="Vehicle inheritance example showing relationships between classes">
</p>

<p align="center">
  <sub>
    Image source:
    <a href="https://takeuforward.org/blogs/oops/what-is-oops">
      TakeUForward – What is OOPs?
    </a>
  </sub>
</p>

### Key Idea

A child class (subclass) inherits and can extend the functionality of a parent class (superclass).

Inheritance can be classified into 5 types which are as follows:
<img width="1042" height="745" alt="image" src="https://github.com/user-attachments/assets/0f511a15-2999-47e1-9e68-fcbcf0feb57a" />
<p align="center">
  <sub>
    Image source: Adapted from
    <a href="https://www.geeksforgeeks.org/interview-prep/oops-interview-questions/">GeeksforGeeks – OOP Interview Questions</a>
  </sub>
</p>


### Review Questions

**1. Why is multiple inheritance not supported with classes in Java?**

<details>
<summary>Show Answer</summary>

To avoid ambiguity, particularly the **Diamond Problem**, where a class could inherit conflicting implementations from multiple parent classes.

</details>

**2. What is multilevel inheritance?**

<details>
<summary>Show Answer</summary>

When a class inherits from another class, which itself inherits from a third class.

For example:

`Animal → Mammal → Dog`

</details>

---
