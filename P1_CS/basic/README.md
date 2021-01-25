# CS Basic

* [What is good code](#What-is-good-code)
* [Object Oriented Programming](#Object-Oriented-Programming)


</br>

## What is good code

If you google it, there is many definition about good code. Here is what people mostly emphasized about "What is good code?"

- Readable(Easy to read and understand for everyone)
- No overlap(extracte each function for same logic)
- Consistent code(Name, Directory)
- Consider the dependencies between code
- Design to be appropriately scalable
- Easy to test 
</br>

## Object Oriented Programming

Looking at the programming paradigm before object-oriented programming, focus was on the computer. It is programming the way computers think. However, object-oriented programming can be said to be a human-focused programming paradigm. In other words, it refers to programming by transferring the real world to programming. Real world objects are regarded as objects, and features necessary for the application to be developed are extracted and programmed from the objects. This is called abstraction.
</br>
If code is written in OOP, the reusability of already written code is high. If frequently used logic is made into a library, it can be used continuously and its reliability can be secured. Also, if the library is well made for various exception situations, even if a developer makes a small mistake, the error can be caught at the compile stage, therefore reducing the occurrence of bugs. In addition, the developer can use the functions provided by the library without knowing how it works internally, which increases productivity. Since the code is divided and written by object unit, debugging is easy and maintenance is easy. In addition, it is easy to map with objects when modeling data, so you can understand the requirements more clearly and program.
</br>
### What to consider for object-oriented design

1. Single Responsibility Principle (SRP): Single Responsibility Principle
    - A class should have only one responsibility, and there should be only one reason for changing a class.
    
2. Open-Closed Principle (OCP): Open-closed principle
    - It must be open for extensions and closed for changes.
    
3. Liskov Substitution Principle (LSP): Liskov Substitution Principle
    - Even if an object of a higher type is substituted with an object of a lower type, the program using the higher type should operate normally.
    
4. ISP (Interface Segregation Principle): Interface segregation principle
    - Interfaces should be separated based on the client using the interface.
    
5. Dependency Inversion Principle (DIP): Dependency Inversion Principle
    - High-level modules should not depend on the implementation of low-level modules.
</br>
