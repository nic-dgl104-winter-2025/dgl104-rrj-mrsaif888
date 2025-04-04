# Research and Reflection Journal
# Week 8
## Activity 1: Language Research
### LUA Programming Language
Lua is a lightweight, high-performance scripting language designed for embedded systems and game development. It is known for its simple syntax, efficiency, and flexibility.
### Key Features of Lua:
* Lightweight & Fast: Small memory footprint, making it ideal for embedded systems.
* Easy to Embed: Used in game engines (like Unity, Roblox, and LOVE2D) and applications.
* Garbage Collection: Manages memory efficiently.
* Dynamic Typing: No need to declare variable types.
* Simple Syntax: Easy to learn and read.

### Basic Syntax 
```
-- Print "Hello, World!"
print("Hello, World!")

-- Variables
name = "Saif"
age = 25

-- Conditional Statement
if age > 18 then
    print(name .. " is an adult.")
else
    print(name .. " is a minor.")
end

-- Loops
for i = 1, 5 do
    print("Number: " .. i)
end

-- Functions
function greet(person)
    return "Hello, " .. person .. "!"
end
print(greet("Saif"))
```

### Why Learn Lua?

* Beginner-friendly syntax.
* High-performance scripting.
* Used in game modding and automation.

### What are some useful resources?
1. Lua Official Website – The primary source for Lua documentation, tutorials, and updates.
2. Programming in Lua (PIL) – A must-read book by Lua's creator, Roberto Ierusalimschy.
3. Lua Reference Manual – Covers all core functionalities.

## Activity 2: User Story 
#### User Story for Spotify’s "Download for Offline Use" feature
As a user, I want to download songs for offline listening, so I can enjoy music without an internet connection.

### 1. Downloading Songs & Playlists

* "As a user, I can download individual songs for offline listening."
* "As a user, I can download entire playlists with one tap."
* "As a user, I can enable automatic downloads for my favorite playlists."

### 2. Managing Downloaded Content

* "As a user, I can view all my downloaded songs in one place."
* "As a user, I can remove downloaded songs to free up storage space."
* "As a user, I can see the storage size of my downloaded songs."
### 3. Offline Playback Experience

* "As a user, I can switch to ‘Offline Mode’ to only see downloaded songs."
* "As a user, I can play my downloaded songs even when I have no internet."
* "As a user, I should get a warning if I try to play an un-downloaded song in offline mode."

### 4. Syncing & Expiry

* "As a user, I can refresh my downloaded songs to maintain my library."
* "As a user, I get notified when a downloaded song is about to expire."
* "As a user, I can redownload expired songs easily."

# Group Project
* Created a group 
* decided the language 
* dividing task for the contribution in the project
  
# Week 9
## Notes
## Design Patterns – Class Notes
### What Are Design Patterns?
* General solutions to common software design problems

* Act as templates or blueprints for writing clean, reusable code

* Mostly used in Object-Oriented Programming (OOP)

### Two Core Principles
* Program to an interface, not an implementation
→ Focus on what an object can do, not how it does it

* Favor composition over inheritance
→ Combine simple objects to build complex ones instead of relying on class hierarchies

### Types of Design Patterns
#### Structural Patterns
* Help organize classes and objects into larger structures

* Focus on how classes are composed

 * Make code more scalable and maintainable

#### Behavioral Patterns
* Help manage communication between objects

* Define how objects interact and respond to events

* Example: Observer Pattern
  
  ### Pattern Examples

  #### Observer Pattern
* One object (Subject) notifies multiple Observers when its state changes

* Used for event handling and real-time updates

 * Use Case: Auction system where bidders (observers) get updates from auctioneer (subject)

#### Singleton Pattern
* Ensures only one instance of a class is created

* Commonly used for shared resources (like database connections)

* Key Features:

1. Private constructor

2. Static instance

3. Public getInstance() method

* Use Case: Database Connection Manager

## Github Issue Summary
For the Identify Issues to Support activity, I found an issue in the React GitHub repo that I think could be a good starting point for contributing.
###  Repository  
**React** – [facebook/react](https://github.com/facebook/react)  
React is a popular open-source JavaScript library developed by Facebook for building user interfaces. It’s widely used for creating fast and interactive web applications, especially single-page apps.

---

###  Issue Chosen  
**Issue**: [Improve documentation for useDeferredValue](https://github.com/facebook/react/issues/28261)

---

###  Why I Chose This Issue

-  The issue is related to documentation, specifically improving the explanation of the `useDeferredValue` hook.
-  The current documentation can be a bit confusing for beginners, and improving it would help a lot of developers understand it better.
-  It’s labeled as a **“good first issue”**, which makes it beginner-friendly and a great way to get involved with an open-source project without needing to dive deep into the core codebase.
-  I enjoy writing and explaining concepts clearly, so this task fits my skills well.
-  Contributing to a major project like React is a great learning experience and a solid way to grow as a developer.
# Group Project
* Create admin panel
* Add functionality of create task and assign teamlead
* create data base connection
  
# Week 10

## Notes
##  MVC Architecture – Class Notes

---

###  What is MVC?

- **MVC** stands for **Model-View-Controller**
- It’s a software design pattern commonly used for building user interfaces
- Purpose: To **separate concerns** — keeping code cleaner, modular, and easier to manage
- Commonly used in **web development frameworks** (like Laravel, ASP.NET, Django)

---

###  Components of MVC

#### 1️ Model – *The Data Layer*

- Handles everything related to **data and business logic**
- Manages how data is:
  - Stored
  - Retrieved
  - Created or updated
- Often interacts with databases or APIs
- Completely **independent** of how data is presented
- Think of it as: **“What the app knows”**
```php
// Example Model - Task.php
class Task {
    private $db;

    public function __construct($db) {
        $this->db = $db;
    }

    public function getAllTasks() {
        return $this->db->query("SELECT * FROM tasks");
    }

    public function createTask($title) {
        $stmt = $this->db->prepare("INSERT INTO tasks (title) VALUES (?)");
        $stmt->execute([$title]);
    }
}

```

#### 2️ View – *The Presentation Layer*

- Deals with the **UI (User Interface)**
- Displays data from the model
- Should not contain any logic for modifying data
- Provides ways for the user to interact (buttons, forms, etc.)
- Like a **display screen** showing what the model provides
```
<!-- Example View - task_view.php -->
<!DOCTYPE html>
<html>
<head><title>Tasks</title></head>
<body>
    <h1>Task List</h1>
    <ul>
        <?php foreach ($tasks as $task): ?>
            <li><?= htmlspecialchars($task['title']) ?></li>
        <?php endforeach; ?>
    </ul>
</body>
</html>

```

#### 3️ Controller – *The Bridge Layer*

- Connects the Model and the View
- Responds to **user input**
- Updates the Model when the user performs actions
- Takes data from the Model and decides **how it should be shown** in the View
- Basically: **“Listens to the user, talks to the Model, and refreshes the View”**
```
// Example Controller - TaskController.php
require_once 'Task.php';

class TaskController {
    private $taskModel;

    public function __construct($db) {
        $this->taskModel = new Task($db);
    }

    public function showTasks() {
        $tasks = $this->taskModel->getAllTasks();
        include 'task_view.php'; // passing data to view
    }

    public function addTask($title) {
        $this->taskModel->createTask($title);
        $this->showTasks();
    }
}

```

### How MVC Works – The Flow

1. **User interacts** with the View (clicks a button, submits a form, etc.)  
2. **Controller handles** the input/action  
3. **Controller updates** the Model (e.g., save a new task, fetch data)  
4. **Model processes** the request and changes the data  
5. **Model notifies** the Controller that data has changed  
6. **Controller updates** the View with new data  
7. **View refreshes** and reflects the updated model to the user



###  Why MVC?

- Keeps code **organized** and **separated**
- Makes projects **scalable** and **easier to debug**
- Developers can work on **Model, View, or Controller independently**
- Great for teamwork and large applications
# Group Project
* Create Teamlead dashboard
* Create backend for the connection and funcationality
* fix bugs for the task creation

# Week 11 OBJECT ORIENTED PROGRAMMING



---

##  What is Object-Oriented Programming?

**Object-Oriented Programming (OOP)** is a programming paradigm that revolves around the concept of "objects", which bundle both data (attributes) and functionality (methods).  

These objects are created from **classes**, and each object is an **instance** of a class. OOP makes it easier to structure and manage complex applications.

Popular OOP languages: **PHP, Python, Java, C++, JavaScript**

---

##  Four Core Principles of OOP

---

### 1️ Encapsulation

- Bundles **data** and **methods** into a single unit (class)
- Restricts direct access to internal state using **access modifiers** (`private`, `public`, `protected`)
- Encourages **modularity** and **data protection**

####  Example (PHP):
```php
class Car {
    private $speed = 0;

    public function accelerate($value) {
        $this->speed += $value;
    }

    public function getSpeed() {
        return $this->speed;
    }
}

$car = new Car();
$car->accelerate(20);
echo $car->getSpeed(); // Output: 20
```
### 2️ Inheritance

- Allows a class (child) to **inherit** properties and methods from another class (parent)
- Promotes **code reuse**
- Supports **hierarchical relationships**
- Child class can **override** or **extend** parent class functionality

####  Example (PHP):
```php
class Vehicle {
    public function honk() {
        echo "Beep beep!";
    }
}

class Bike extends Vehicle {
    public function ride() {
        echo "Riding the bike!";
    }
}

$bike = new Bike();
$bike->honk();  // Output: Beep beep!
$bike->ride();  // Output: Riding the bike!

```
### 3️ Polymorphism

- Means **“many forms”**
- Allows different classes to define the same method in **different ways**
- Achieved using **method overriding**, **interfaces**, or **abstract classes**

####  Example (PHP):
```php
class Animal {
    public function speak() {
        echo "Some sound";
    }
}

class Dog extends Animal {
    public function speak() {
        echo "Woof!";
    }
}

class Cat extends Animal {
    public function speak() {
        echo "Meow!";
    }
}

$dog = new Dog();
$cat = new Cat();
$dog->speak(); // Output: Woof!
$cat->speak(); // Output: Meow!
```
### 4️ Abstraction

- Focuses on **hiding complex details** and showing only **essential features**
- Achieved using **abstract classes** or **interfaces**
- Forces child classes to **implement** specific methods

####  Example (PHP):
```php
abstract class Shape {
    abstract public function area();
}

class Circle extends Shape {
    private $radius;

    public function __construct($r) {
        $this->radius = $r;
    }

    public function area() {
        return 3.14 * $this->radius * $this->radius;
    }
}

$circle = new Circle(5);
echo $circle->area(); // Output: 78.5
```
###  Benefits of OOP

-  Code **reusability**
-  Better **modularity** and **debugging**
-  Improved **data security** using encapsulation
-  Easier to **maintain** and **scale**
-  Closer to **real-world modeling**

---

###  Real-Life Example

```php
class User {
    private $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function greet() {
        return "Hello, " . $this->name;
    }
}

$student = new User("Saif");
echo $student->greet(); // Output: Hello, Saif
```
###  References

- [W3Schools – PHP OOP](https://www.w3schools.com/php/php_oop_what_is.asp)
- [MDN – Object-Oriented Programming](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_programming)
- [GeeksForGeeks – OOP Concepts](https://www.geeksforgeeks.org/object-oriented-programming-in-php/)

# Group Project
* Create user dashboard
* Complete the backend functionality 
* Add components 
  
# Week 12
#  Functional Programming – Class Notes with Examples

---

##  What is Functional Programming?



- The **Functional Programming (FP) Paradigm** focuses on writing programs using **pure functions**, **immutability**, and **function composition**.
- Once mostly used in **academic research**, FP is now widely used in **web and mobile app development** — both on the **backend** and even in **front-end frameworks**.
- It is not just about using “functional languages” like Haskell, but also about using **functional tools** available in modern programming languages.

---

##  Functional Tools in Modern Programming

- Today, languages like **Java, JavaScript, Kotlin, Swift, Python**, and many more support **functional-style APIs**.
- These tools are especially powerful when working with **collections** (arrays, lists, etc.).
- They help write more **concise**, **readable**, and **efficient** code by replacing verbose loops with declarative methods.

---

##  Common Functional Methods (with JavaScript Examples)

### 1️ `map()`

- Transforms each item in a collection and returns a new collection.

```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2);
console.log(doubled); // Output: [2, 4, 6]
```
### 2️ `filter()`

- Filters elements in a collection based on a condition.
- Returns a **new array** containing only the elements that satisfy the condition.

####  Example (JavaScript):
```javascript
const numbers = [1, 2, 3, 4];
const evens = numbers.filter(n => n % 2 === 0);
console.log(evens); // Output: [2, 4]
```
### 3️ `reduce()`

- Combines all elements of a collection into a **single value**
- Often used for summing, multiplying, or aggregating values

####  Example (JavaScript):
```javascript
const numbers = [1, 2, 3, 4];
const total = numbers.reduce((acc, curr) => acc + curr, 0);
console.log(total); // Output: 10

```
###  Why Use Functional Tools?

-  More **concise** than traditional `for` or `while` loops  
-  Helps you focus on **what** you want to do, not **how**  
-  Encourages **clean**, **modular**, and **testable** code  
-  Makes code **easier to read and reason about**
###  Usage of Functional Programming In Real-World

Functional programming isn't just a theoretical concept — it's widely used in real-world applications and tools. Many modern companies and technologies adopt functional principles to improve code reliability, scalability, and maintainability.

####  Examples of Real-World Use:

- **Frontend Development**:  
  Libraries like **React.js** use functional components and hooks, encouraging pure functions and immutability.

- **Backend Systems**:  
  Languages like **Elixir** and **Scala** are used in scalable backend systems (e.g., **WhatsApp**, **Twitter**).

- **Data Processing**:  
  Functional patterns are used in **data pipelines** with tools like **Apache Spark** and **MapReduce** (e.g., at **Google**, **Netflix**).

- **Mobile Development**:  
  Languages like **Kotlin** (Android) and **Swift** (iOS) support functional constructs like `map`, `filter`, and `reduce`.

- **Functional APIs in Mainstream Languages**:  
  Even in traditionally object-oriented languages like **Java**, FP is adopted through features like **Streams API**, `lambda` expressions, and method references.

####  Summary:

Functional programming concepts such as **immutability**, **pure functions**, and **higher-order functions** are not just academic — they’re being used in real projects to build efficient, scalable, and reliable software.


###  References

- [MDN – Functional Programming](https://developer.mozilla.org/en-US/docs/Glossary/Functional_programming)  
- [JavaScript.info – Array Methods](https://javascript.info/array-methods)  
- [GeeksForGeeks – Functional Programming Paradigm](https://www.geeksforgeeks.org/functional-programming-paradigm/)  
- [FreeCodeCamp – Functional Programming in JavaScript](https://www.freecodecamp.org/news/functional-programming-in-js-with-practical-examples-part-1-87c2b0dbc276/)  
- [Eloquent JavaScript – Higher-Order Functions](https://eloquentjavascript.net/05_higher_order.html)

# Group Project
* Change the front end design of the project 
* divide the task for debugging the project 
  
# Week 13

# Group Project
* Fix issues that were creating problem 
* Test the project 

# Week 14 
* write readme file for the project