> The main reason Scala is used in this book is to be able to demonstrate multiple paradigms in a single language.

# Procedural Programming
* Go is primarily procedural in nature.
* Procedural programming is a linear idiom where code is written and executed top-down, similar to following a recipe.
* This top-down approach is known as **hierarchical decomposition**.
* Procedural programming can be categorized as a subset or implementation of **structured programming**.
---
## GO
> Go (or Golang) is a programming language designed by Google in 2007 with a goal of introducing a language that was simple, hyperproductive, and high performance primarily for systems administrators working on servers that hosted web applications.
### A demonstration of structured procedural programming
```scala
// non-structured
def isMMA(fightingType: String): Boolean = {
    if(fightingType == "boxing"){
        return false
    }
    if(fightingType == "Tai Chi"){
        return false
    }
    if(fightingType == "Jeet Kune Do"){
        return true
    }
    return false
}

// structured
def isMMA(fightingType: String): Boolean = {
    if(fightingType == "boxing"){
        false
    }
    else if(fightingType == "Tai Chi"){
        false
    }
    else if(fightingType == "Jeet Kune Do"){
        true
    }
    else {
        false
    }
}
```
- The structured version of the function has a **single entry point** and a **single exit point**.
- Each branch is mutually exclusive.
- Scala can imply the return value from the last line, so `return` can be eliminated.
- The non-structured version lacks an exclusive execution path and must explicitly use `return`.
---
## Why Procedural Programming Is Common

- It is **easy to follow** and clear to read.
- Thinking in chronological sequences is natural and intuitive.
- Keeping programs simple and intuitive enables long-term **maintainability** and **collaboration**.
- Procedural programs tend to be lightweight with less compile-time and runtime overhead.
- They align with the idea of creating programs that do one thing well.
- They require less architectural coordination and make debugging easier.
---
## Application State and Mutation

- Procedural programs often require **mutation** of application state.
- **Application state** is the value of variables at different times during program execution.
- If a procedural program crashes and restarts, the application state resets to the initialized state.
- Example: the Nebula OS script initializes `command` and mutates it as the program runs.
---
## Problems with Global State

- As procedural programs grow, holding state in a global context becomes difficult.
- Developers may encounter **namespace collisions**.
- Developers may unintentionally update a variable's state without realizing it exists elsewhere.
- This can lead to runtime semantic errors.
- **Mutation is dangerous** for these reasons.
---
## Relation to Other Paradigms
- **Object-oriented programming** and **functional programming** attempt to remedy the danger of mutation through encapsulation and pure functions.
- Large OOP or functional programs can still contain procedural aspects.
- Overly complex programs can sometimes be safely refactored into simple, linear procedures.