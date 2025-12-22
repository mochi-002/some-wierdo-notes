# Introduction of Programming Paradigms

A **programming paradigm** is a methodology for problem-solving using the tools and techniques available to us, following a particular approach.

![[Pasted image 20251205181308.png]]

---

## Imperative Programming Paradigm

> It is one of the oldest programming paradigms, featuring a close relation to machine architecture.  
> It is based on Von Neumann architecture, works by changing the program state through assignment statements, performs step-by-step tasks by changing state, and focuses mainly on how to achieve the goal.  
> The paradigm consists of several statements, and after execution, the result is stored.

### Advantages
1. Very simple to implement
2. It contains loops, variables, etc.

### Disadvantages
1. Complex problems cannot be solved 
2. Less efficient and less productive
3. Parallel programming is not possible

### Example
```python
def main():
    # Array to store marks
    marks = [12, 32, 45, 13, 19]

    # Variable to store the sum of marks
    total_marks = sum(marks)

    # Calculate the average
    average = total_marks / len(marks)

    # Output the average
    print("Average of five numbers:", average)

if __name__ == "__main__":
    main()
```

#### Output
```text
Average of five numbers: 24.2
```

---

## Procedural Programming Paradigm

> This paradigm emphasizes procedure in terms of underlying machine model.  
> There is no difference between procedural and imperative approach.  
> It allows code reuse and was a boon at the time because of its reusability.

### Example

```python
# Prompt user to enter a number
num = int(input("Enter any Number: "))

fact = 1  # Initialize factorial variable

# Calculate factorial
for i in range(1, num + 1):
    fact = fact * i

# Print the factorial
print("Factorial of", num, "is:", fact)
```

---

## Object Oriented Programming (OOP)

> The program is written as a collection of classes and objects meant for communication.  
> The smallest and basic entity is the object, and all computation is performed on objects.  
> More emphasis is on data rather than procedure.  
> It can handle almost all real-life problems in modern scenarios.

### Advantages

1. Data security
2. Inheritance
3. Code reusability
4. Flexible and supports abstraction

### Example

```python
class Signup:
    def __init__(self):
        self.userid = 0
        self.name = ""
        self.emailid = ""
        self.sex = ""
        self.mob = 0

    def create(self, userid, name, emailid, sex, mob):
        print("Welcome to GeeksforGeeks\nLets create your account\n")
        self.userid = 132
        self.name = "Radha"
        self.emailid = "radha.89@gmail.com"
        self.sex = 'F'
        self.mob = 900558981
        print("your account has been created")


if __name__ == "__main__":
    print("GfG!")
    s1 = Signup()
    s1.create(22, "riya", "riya2@gmail.com", 'F', 89002)
```

#### Output

```
GfG!
Welcome to GeeksforGeeks
Lets create your account

your account has been created
```

---

## Parallel Processing Approach

> The processing of program instructions by dividing them among multiple processors.  
> A parallel processing system possesses many processors with the objective of running a program in less time by distributing tasks.  
> This approach is similar to divide and conquer.

### Advantages

1. Speed & Performance
2. Efficiency
3. Redundancy

### Example (Using Manual Threading)

```cpp
#include <iostream>
#include <vector>
#include <thread>
#include <numeric> // For std::accumulate

// Function to sum a portion of a vector
void sum_part(const std::vector<int>& vec, size_t start, size_t end, long long& result) {
    result = 0;
    for (size_t i = start; i < end; ++i) {
        result += vec[i];
    }
}

int main() {
    const int N = 100000000;
    std::vector<int> data(N, 1);

    // Divide work for two threads
    size_t mid = N / 2;
    long long sum1, sum2;

    // Create and start threads
    std::thread t1(sum_part, std::ref(data), 0, mid, std::ref(sum1));
    std::thread t2(sum_part, std::ref(data), mid, N, std::ref(sum2));

    // Wait for threads to finish (join)
    t1.join();
    t2.join();

    long long total_sum;
```

---

## Declarative Programming Paradigm

> It is divided into Logic, Functional, and Database.  
> In computer science, **declarative programming** is a style of building programs that expresses logic of computation without describing its control flow.  
> It considers programs as theories of some logic and may simplify writing parallel programs.  
> The focus is on _what_ needs to be done rather than _how_ it should be done.  
> This is the main difference between imperative (how to do) and declarative (what to do) paradigms.

---

## Logic Programming Paradigms

> It can be termed as an abstract model of computation.  
> It solves logical problems like **puzzles**, **series**, etc.  
> In logic programming, we have a predefined **knowledge base** and the machine produces results based on the question + knowledge base.  
> Traditional programming languages do not have this concept, but in AI/ML we have models like the **Perception** model that use similar mechanisms.  
> Logic programming emphasizes _knowledge base_ and _the problem_.  
> Execution resembles proving a **mathematical statement**, e.g., Prolog.

### Example

```prolog
predicates  
  sumoftwonumber(integer, integer).  
clauses  
  sumoftwonumber(0, 0).  
  sumoftwonumber(N, R) :-  
    N > 0,  
    N1 is N - 1,  
    sumoftwonumber(N1, R1),  
    R is R1 + N.
```

---

## Functional Programming Paradigms

> The functional programming paradigm has its roots in mathematics and is language independent.  
> The key principle is executing a series of mathematical functions.  
> Functions are the main model for abstraction and not data structures.  
> Data is loosely coupled to functions, and functions hide their implementation.  
> A function can be replaced with its value without changing the program's meaning.  
> Languages like **Perl** and **JavaScript** often use this paradigm.

### Example

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)

print(factorial(5))  # Output: 120
```

---

## Database / Data-Driven Programming Approach

> This programming methodology is based on data and its movement.  
> Program statements are defined by data rather than hard-coded steps.  
> Database programs are core to business information systems and handle file creation, data entry, update, query, and reporting.  
> Several languages are designed for database applications — such as **SQL**.  
> It is applied to streams of structured data for filtering, transforming, aggregating, or calling other programs.

### Example

```sql
CREATE DATABASE databaseAddress;  
CREATE TABLE Addr (  
    PersonID int,  
    LastName varchar(200),  
    FirstName varchar(200),  
    Address varchar(200),  
    City varchar(200),  
    State varchar(200)  
);
```

---