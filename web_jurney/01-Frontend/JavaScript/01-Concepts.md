```dataviewjs
const tasks = dv.current().file.tasks;
const total = tasks.length;
const done = tasks.where(t => t.completed).length;
const progress = total > 0 ? Math.round((done / total) * 100) : 0;

dv.paragraph(`**JavaScript Progress • ${done}/${total} (${progress}%)**`);

const barHtml = `
<div style="
  background: #f0f0f0;
  height: 24px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: inset 0 1px 3px rgba(0,0,0,0.1);
  margin: 10px 0;">
  <div style="
    height: 100%;
    width: ${progress}%;
    background: linear-gradient(to right, #667eea, #764ba2);
    border-radius: 12px;
    box-shadow: 0 0 10px rgba(102, 126, 234, 0.5);
    transition: width 0.6s ease;">
  </div>
</div>`;

dv.el("div", barHtml);
```
## 1️⃣ JavaScript Basics & Environment
- [x] What is JavaScript
- [x] What JavaScript can do
- [x] How to study JavaScript
- [x] Required tools & setup
- [x] Chrome Developer Tools
- [x] Where to write JavaScript code
- [x] Comments & bad practices
- [x] Output to screen
- [x] Console methods & styling
- [x] Web APIs overview
- [x] ECMAScript (ES)

## 2️⃣ Data Types & Variables
- [x] JavaScript data types
- [x] typeof operator
- [x] Variables introduction
- [x] Identifier naming rules
- [x] var vs let vs const
- [x] Type coercion

## 3️⃣ Strings
- [x] String syntax
- [x] Escape sequences
- [x] String concatenation
- [x] Template literals
- [x] String methods
- [x] String challenges

## 4️⃣ Numbers & Math
- [x] Numbers in JavaScript
- [x] Number methods
- [x] Math object
- [x] Arithmetic operators
- [x] Unary plus & negation
- [x] Assignment operators
- [x] Number challenges

## 5️⃣ Operators & Conditions
- [x] Comparison operators
- [x] Logical operators
- [x] Nullish coalescing operator
- [x] If / Else conditions
- [x] Nested if conditions
- [x] Ternary operator
- [x] Switch statement
- [x] Conditions challenges

## 6️⃣ Arrays
- [x] Array introduction
- [x] Array length
- [x] Add & remove elements
- [x] Sorting arrays
- [x] Slicing arrays
- [x] Joining arrays
- [ ] Array challenges

## 7️⃣ Loops
- [x] for loop
- [x] Looping over sequences
- [x] Nested loops
- [x] Break, continue & labels
- [x] Advanced loop examples
- [x] while loop
- [x] do...while loop
- [x] Loop challenges
- [x] Practical loop projects

## 8️⃣ Functions
- [x] Function basics
- [x] Advanced function examples
- [x] Return statement
- [x] Default parameters
- [x] Rest parameters
- [x] Anonymous functions
- [x] Arrow functions
- [x] Nested functions
- [x] Function challenges

## 9️⃣ Scope
- [x] Global scope
- [x] Local scope
- [x] Block scope
- [x] Lexical scope

## 🔟 Higher-Order Functions
- [x] map()
- [x] filter()
- [x] reduce()
- [x] forEach()
- [x] Higher-order function challenges

## 1️⃣1️⃣ Objects
- [x] Object introduction
- [x] Dot vs bracket notation
- [x] Nested objects
- [x] this keyword
- [x] Constructor functions
- [x] new keyword
- [x] Object.create()
- [ ] Object.assign()

## 1️⃣2️⃣ DOM (Document Object Model)
- [x] What is DOM
- [x] Select elements
- [x] Get & set content
- [x] Get & set attributes
- [x] Check attributes
- [x] Create & append elements
- [x] Deal with children
- [x] DOM events
- [x] Form validation
- [x] Event simulation
- [x] ClassList methods
- [x] Styling with JS
- [x] Insert & remove elements
- [x] DOM traversing
- [x] DOM cloning
- [x] addEventListener()
- [ ] DOM challenges

## 1️⃣3️⃣ BOM (Browser Object Model)
#### Topics
- [x] What is BOM ✅ 2025-12-22
- [x] Alert, confirm, prompt ✅ 2025-12-22
- [x] setTimeout & clearTimeout ✅ 2025-12-22
- [x] setInterval & clearInterval ✅ 2025-12-22
- [x] window.location ✅ 2025-12-22
- [x] Window open & close ✅ 2025-12-22
- [x] Window history ✅ 2025-12-22
- [x] Scroll methods ✅ 2025-12-22
- [x] Focus, print, stop ✅ 2025-12-22
- [x] Local Storage ✅ 2025-12-23
- [x] Session Storage ✅ 2025-12-23
- [x] BOM challenges ✅ 2025-12-23
#### Assignments
- [x] [From 102 to 110](https://elzero.org/javascript-bootcamp-assignments-lesson-from-102-to-110/) ✅ 2025-12-23 -> [[04-Assignments]]
- [x] [From 111 to 114](https://elzero.org/javascript-bootcamp-assignments-lesson-from-111-to-114/) ✅ 2025-12-23 -> [[04-Assignments]]
---
## 1️⃣4️⃣ Destructuring & Spread
#### Topics
- [x] Array destructuring ✅ 2025-12-24
- [x] Object destructuring ✅ 2025-12-24
- [x] Function parameters destructuring ✅ 2025-12-24
- [x] Swap variables ✅ 2025-12-24
- [x] Mixed destructuring ✅ 2025-12-24
- [x] Spread syntax ✅ 2025-12-24

#### Asignments
- [x] [From 115 to 122](https://elzero.org/javascript-bootcamp-assignments-lesson-from-115-to-122/) ✅ 2025-12-24 -> [[04-Assignments]]
---
## 1️⃣5️⃣ Advanced Data Structures
- [ ] Set
- [ ] WeakSet
- [ ] Map
- [ ] Map methods
- [ ] WeakMap
- [ ] Array.from()
- [ ] copyWithin()
- [ ] some()
- [ ] every()
- [ ] Data structure challenges

## 1️⃣6️⃣ Regular Expressions (Regex)
- [ ] Regex basics
- [ ] Modifiers
- [ ] Ranges
- [ ] Character classes
- [ ] Quantifiers
- [ ] Replace patterns
- [ ] Form validation
- [ ] Regex challenges

## 1️⃣7️⃣ Object-Oriented Programming (OOP)
- [ ] OOP principles
- [ ] Constructor functions
- [ ] Classes
- [ ] Static properties & methods
- [ ] Inheritance
- [ ] Encapsulation
- [ ] Prototypes
- [ ] Prototype chain
- [ ] Object descriptors

## 1️⃣8️⃣ Date, Time & Generators
- [ ] Date & time basics
- [ ] Get date & time
- [ ] Set date & time
- [ ] Formatting date
- [ ] Track execution time
- [ ] Generator functions
- [ ] Delegate generators
- [ ] Infinite generators

## 1️⃣9️⃣ Modules
- [ ] ES Modules
- [ ] Import & export
- [ ] Named vs default exports

## 2️⃣0️⃣ JSON & APIs
- [ ] JSON basics
- [ ] JSON syntax
- [ ] JSON vs JS Object
- [ ] JSON.parse()
- [ ] JSON.stringify()
- [ ] API concept

## 2️⃣1️⃣ Asynchronous JavaScript
- [ ] Sync vs Async
- [ ] Call stack
- [ ] Web APIs
- [ ] Event loop
- [ ] Callback queue
- [ ] AJAX
- [ ] XHR
- [ ] Fetch API
- [ ] Looping over API data

## 2️⃣2️⃣ Promises & Async/Await
- [ ] Callback hell
- [ ] Promises
- [ ] then / catch / finally
- [ ] Promises with XHR
- [ ] Promise.all()
- [ ] Promise.allSettled()
- [ ] Promise.race()
- [ ] async
- [ ] await
- [ ] try / catch / finally