
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

## Abstraction

**Abstraction** displays only the necessary information while hiding internal implementation details.

**Real-world example: Driving a Car**

A person can drive a car using the steering wheel, brakes, and accelerator without understanding how the engine or other internal components work.

<p align="center">
  <img src="https://github.com/user-attachments/assets/5115b926-4d76-4cf0-9930-9b2f308298fc"
       width="700"
       alt="Car illustrating the concept of abstraction">
</p>

<p align="center">
  <sub>
    Image source:
    <a href="https://takeuforward.org/blogs/oops/what-is-oops">TakeUForward – What is OOPs?</a>
  </sub>
</p>

**Key Idea:** Focus on *what an object does*, rather than *how it works internally*.

### Review Questions

**1. How is abstraction achieved in Java?**

<details>
<summary>Show Answer</summary>

Using **abstract classes** and **interfaces**.

</details>

**2. Can we create an object of an abstract class?**

<details>
<summary>Show Answer</summary>

No. Abstract classes cannot be instantiated directly.

</details>

**3. Can abstract classes have concrete methods?**

<details>
<summary>Show Answer</summary>

Yes. Abstract classes can contain both abstract methods (without a body) and concrete methods (with a body).

</details>

---
