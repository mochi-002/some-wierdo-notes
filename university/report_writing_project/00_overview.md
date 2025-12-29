---
topic: Programming Paradigms
date: 05-Dec-2025
course: Report Writing
tags:
  - studies
---
# Software Engineering from Scratch 171 -> 208

## Key Concepts
- [Introduction of Programming Paradigms](part_0_programming_paradigms.md)
- [Procedural Prigramming](part_1_procedural_programming.md)
- [Object-Oriented Programming](part_2_oop.md)
- [Functional Programming](part_3_functional_programming.md)
- [Summary](part_4_summary.md)
## Important Details
- **Programming Paradigm**: A methodology for problem-solving using specific tools and approaches.
- **Imperative/Procedural Paradigm**: Focuses on step-by-step instructions; simple but not suitable for complex/parallel problems.
- **Object-Oriented Programming (OOP)**: Centers on classes and objects; emphasizes encapsulation, inheritance, polymorphism, and abstraction.
- **Functional Programming (FP)**: Rooted in mathematics; emphasizes pure functions, immutability, and higher-order functions.
- **Parallel Processing**: Divides tasks among multiple processors to improve speed and efficiency.
- **Declarative/Logic/Database Paradigms**: Focus on *what* to do rather than *how*; logic programming uses knowledge bases; data-driven programming relies on structured data for operations.

## Examples
- **Imperative/Procedural**
```python
marks = [12, 32, 45, 13, 19]
total_marks = sum(marks)
average = total_marks / len(marks)
print("Average:", average)
```

- **Procedural Factorial**
```python
num = int(input("Enter number: "))
fact = 1
for i in range(1, num + 1):
    fact *= i
print("Factorial:", fact)
```

- **OOP Example**
```python
class Signup:
    def __init__(self):
        self.userid = 0
    def create(self):
        self.userid = 132
```

- **Functional Programming (Recursion)**
```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n - 1)
print(factorial(5))
```

- **Higher-Order Function Example**
```scala
def repeat(n: Int)(func: => Unit){
  if(n > 0){ func; repeat(n-1)(func) }
}
repeat(3){ println("Hello") }
```

- **FP Built-in Functions**
```scala
data.foreach(println)
data.map(_.toUpperCase)
data.filter(_(1).asInstanceOf[Int] > 140)
data.reduce(_+_)
data.fold(100)(_+_)
```

- **Parallel Processing (C++ Threads)**
```cpp
std::thread t1(sum_part, ...);
std::thread t2(sum_part, ...);
t1.join(); t2.join();
```

- **Declarative/Logic Programming (Prolog)**
```prolog
sumoftwonumber(0,0).
sumoftwonumber(N,R):- N>0, N1 is N-1, sumoftwonumber(N1,R1), R is R1+N.
```

- **Database Example (SQL)**
```sql
CREATE TABLE Addr(PersonID int, LastName varchar(200), ...);
```

## Questions
- What are the main differences between procedural, OOP, and functional paradigms?
- When should parallel processing be preferred over sequential execution?
- How do higher-order functions improve code reusability in FP?
- What are the advantages and trade-offs of using abstract classes and interfaces?

## Summary
- Programming paradigms define the approach to problem-solving.
- Procedural programming is simple, top-down, and mutable; good for straightforward tasks.
- OOP encapsulates data and methods, provides reusability and maintainability, supports inheritance and polymorphism.
- Functional programming emphasizes pure functions, immutability, and higher-order functions, minimizing side effects.
- Parallel and declarative paradigms optimize performance and reasoning about code.
- Choosing a paradigm depends on complexity, maintainability, and project requirements.

## Related Topics
- [Introduction of Programming Paradigms](part_0_programming_paradigms.md)
- [Procedural Prigramming](part_1_procedural_programming.md)
- [Object-Oriented Programming](part_2_oop.md)
- [Functional Programming](part_3_functional_programming.md)
- [Summary](part_4_summary.md)