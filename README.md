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

Private constructor

Static instance

Public getInstance() method

* Use Case: Database Connection Manager


