
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
