# CS Basic

[TOC]

* [What is good code?](#What-is-good-code)
* [Object Oriented Programming](#Object-Oriented-Programming)
* [RESTful API](#RESTful-API)
* [Functional programming](#Functional-programming)
* [What is MVC pattern?](#What-is-MVC-pattern?)


</br>

## What is good code?

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


## RESTful API

REST stands for REpresentational State Transfer. Here, it is used as an API that wraps the adjective type ending of ~ful. In other words, service design that faithfully adheres to the basic principles of REST can be expressed as'RESTful'.

</br>

REST is a design pattern, architecture There are many stories, but it can be seen as one architecture. More precisely, REST is a Resource Oriented Architecture. It is designed to process resources through HTTP Method, where resources are used at the center of API design.

</br>

### REST 6 principles
- Uniformed interface
- Stateless
- Caching
- Client server
- Hierarchical system
- Code on demand

</br>

### What does it mean to design an API in a RESTful way?
</br>

1. Explicit and intuitive separation of resources and actions.
- Resources are expressed as URIs, and what the resource points to must be expressed as a noun.
- Actions are expressed in HTTP Method, and GET (retrieve), POST (create), PUT (complete modification of existing entity), PATCH (partial modification of existing entity), and DELETE (delete) are used for clear purposes.

2. Message uses header and body clearly separated.
- The contents of the entity are contained in the body.
- The API version information, which is the control information that is the basis for the application server to act, and the MIME type to receive a response, are included in the header.
- Header and body can be divided into http header and http body, or can be divided into json structure that enters the http body.
3. Manage the API version.
- Note that the API's signature may change because the environment is always changing.
- When changing a specific API, you must ensure backward compatibility.
4. Let the server and the client make requests using the same method.
- The browser sends form-data type submit and the server sends it as json rather than separate expressions.
- In other words, the URI must be platform neutral.

</br>

### What are the advantages?
- Easy to provide Open API
- Multiplatform support and easy linkage.
- You can send and receive data in any type.
- Existing web infrastructure (HTTP) can be used as it is.

</br>

### What are the disadvantages?
- There are only 4 methods available.
- Not suitable for distributed environment.
- It supports only HTTP communication model.

</br>

## Functional programming

### immutable vs mutable
</br>
First of all, you need to understand the difference between immutable and mutable. An immutable object means an object that cannot change the value of the object. When the value changes, a new object must be created and the changed value injected and returned. Unlike this, mutable objects change their values when the corresponding object values change.

</br>

### First-citizen
</br>

In a language that follows the functional programming paradigm, a function is considered a first class citizen. The first class object is as follows.

Functions can be contained in variables or data structures, so they can be passed as parameters of functions and can be used as return values of functions.
Unique identification is possible regardless of the name used for the assignment.
Functions can be defined directly as literals.

</br>

### Reactive Programming

Reactive programming, also called declarative programming, is the opposite of imperative programming. It also refers to using the functional programming paradigm. Reactive programming basically sees everything as a stream. A stream can be viewed as a set of values, and data can be managed immutable through the provided functional method.

</br>

### Why Functional Programming (again)?

Perhaps this is because functional programming has an advantage in dealing with ‘concurrency’ as multi-core became the basis. If multi-threaded programming was a problem that should be avoided as possible until only a few years ago, it has become a basis that must be considered now. However, many common developers still find it difficult. I am less ready. But on the one hand, isn't it because the language we use makes the problem more complicated?
In object-oriented programming based on side effect, it is not easy to effectively cope with multithreading, but functional programming that mainly deals with immutable values ​​inherently makes concurrency processing easier.
However, I think this part can actually be thought of as another subject called 'Concurrency Oriended Programming'. This is because the method of solving concurrency in the Go language cannot be regarded as a functional programming method, and it has a different shape from OO or FP.
</br>

So, why is functional programming attracting attention again now? Personally, I think it may be because of the expressive power of functional programming'language'. Although functional programming is possible in Python or Java, it is not recommended to do this because there is little gain in expressive power due to language limitations.
In addition to this, if we approach the homogeneity problem mentioned above, it can be seen that functional languages ​​support the concurrency problem better because it effectively abstracts and provides a library or idiom to support concurrency programming.
In addition to this, the essential advantages of functional programming are that it is easier to maintain and understand the code compared to the code that relies on side-effects.

</br>


## What is MVC pattern?

</br>

### Role of each component of MVC <Who, When, What>



- Model

When called by the controller, it plays the role of the request. It is an area that implements business logic and is a part that processes data in an application program. Business logic can be said to be a part of an application program that processes data necessary for work. It connects to the DB and extracts, saves, deletes, updates, and converts data. When there is a state change, it notifies the controller and the view so that they can receive follow-up orders.



- Controller (View in Django)

It can be called a mediator. When a client's request is received, the model component that actually performs the task is called for that request. Also, if there is data sent by the client, it processes the data to make it easier to pass to the model. When the model is done, it passes the result to the view.






- View (Template in Django)

It takes the result of the model received from the controller and creates a screen to be displayed to the user. The created screen is sent to the web browser and the web browser displays it. It is an area that displays extracted data or general text data as a part displayed on the screen, or displays an input form or an interface for interaction with a user.

</br>

### How does MVC work?

</br>

When a request is made in C/S (Client-Server) structure, it is based on a structure that responds accordingly.

1. The web browser requests the web server to run the web application. (You can think of the MVC structure as WAS.)

2. The web server finds a servlet that can handle the incoming request and delivers the request. (Matching)

3. The servlet calls the method of the model Java object.

4. Create a value object by processing data, or create a value object through interaction with a database using JDBC.

5. Return the result value of completing the task to the controller

6. The controller delivers the result value received from the model to the View.

7. JSP creates a result screen to be displayed by referring to the received value and delivers it to the controller.

8. The screen received from the view is delivered to the web server.

9. When the web browser receives the request result value from the web server, it displays the value on the screen.