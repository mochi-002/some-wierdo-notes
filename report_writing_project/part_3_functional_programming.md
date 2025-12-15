> Haskell, Clojure, and early forms of JavaScript are great examples of common languages which follow the functional programming paradigm
# Funtional Programming
- Functional programming is a paradigm whose roots date back to the concepts of lambda calculus in the 1930s.
- The main objective of functional programming is to minimize (or eliminate entirely) “side effects.”
	- A “side effect,” in programming, is an action that mutates the existing state of the application whether that be changing a variable or a piece of a data structure stored in memory.
	- The motivation behind removing side effects is to eliminate errors in your code. If, for example, multiple functions within a code base are accessing a global variable and one of those functions mutates the variable without the other function knowing about the change, it could create some runtime semantic errors.
- Core idea of functional programming is to solve complexity like OOP but with shorter, less error-prone code.
- Programs are written as **inputs and outputs** to mathematical functions and all variables and data structures are **immutable**.
### Code smells indicating mutation
1. Functions with **no input parameters**.
2. Functions with **no return type**.
3. Explicit imports of **mutable data structures**.
4. Using many **var** assignments instead of **val**.
---
## Pure functions
- A function is said to be a “pure function” if, and only if, it takes in inputs and returns an output without mutating application state in the process.
- Pure functions are guaranteed to always return the same result for the same inputs.
#### Representation of duplicating an object rather than mutating it in the functional programming paradigm 
```scala
package CombatGame
object funcs extends App {
    def attack(opponent: Fighter, damage: Int): Fighter = {
         return new Fighter(opponent.weapon, opponent.hp -
damage)
    }
}
```
- Instead of mutating the opponent’s `hp` directly, the function creates a **new Fighter object**.
- The new object uses:
    - the same weapon
    - hp = old hp − damage
- This avoids applying **side effects** to the original Fighter.
---
## Higher-Order Functions
- One of the benefits of writing applications in the functional programming style is that it affords you the opportunity to write extremely rich expressions. By doing so, oftentimes you will see functional programs that lack any procedural style.
- A higher-order function, in its most basic form, is simply a function that either takes another function as its input or returns a function (or both).
#### A higher-order function repeat that takes a function to be repeated as one of its inputs
```scala
def repeat(n: Int, iter: Int = 0)(func: => Unit){
     if(iter < n) {
         func
         repeat(n, iter + 1)(func)
     }
}
val dagger = new Dagger()
repeat(3){ println(dagger.attackDamage) }
```
---
```text
Terminal Output
5
5
5
```
- This repeat function actually demonstrates two useful principles of functional programming. 
	- First, notice that it takes a second set of parameters: the function to be repeated, n representing the number of times you want the function to repeat. 
	- Second thing to notice in this higher-order function is that it calls itself.
---
## Built in higher order functions
### foreach
>The foreach function is a function that can be applied to a collection of data. Often in functional programming, foreach is used as a replacement for the traditional loop or recursion when the loop or recursion is simply meant to continue looping until it reaches the end of a collection of data.
```scala
val data = List("Bruce Lee", "Chuck Norris", "Chuck Liddell", "Ronda Rousey")

def printFighter(fighter: String): Unit = {
    println(fighter)
}
data.foreach(printFighter)
data.foreach(println)
data.foreach((fighter) => { println(fighter) })
data.foreach(fighter => println(fighter))
// Each of these four methods of calling the foreach function results in the same action
```
### map
>It is useful to map over a collection if you wish to change something about some or all of the items in the collection
```scala
val data = List("Bruce Lee", "Chuck Norris", "Chuck Liddell", "Ronda Rousey")
val formattedData = data.map(fighter => fighter.toUpperCase)
println(formattedData)
```
---
```text
Terminal Output
List(BRUCE LEE, CHUCK NORRIS, CHUCK LIDDELL, RONDA ROUSEY)
```
### flatmap
>The flatMap function operates very similar to a map function.
>The difference is that the flatMap function can operate on data structures that are nested.
```scala
val data = List(List("Bruce Lee", 141), List("Chuck Norris",170), List("Chuck Liddell", 205), List("Ronda Rousey", 134))
val flattenedData = data.flatMap(item => item)
println(flattenedData)
```
---
```text
Terminal Output
List(Bruce Lee, 141, Chuck Norris, 170, Chuck Liddell, 205,Ronda Rousey, 134)
```
### filter
>The filter function is similar to the map function; however, the anonymous function that is passed to filter must return a Boolean value. Any individual item that returns a true value during its iteration through the list will end up in the resulting new collection
```scala
val data = List(List("Bruce Lee", 141), List("Chuck Norris", 170), List("Chuck Liddell", 205), List("Ronda Rousey", 134))
val filteredData = data.filter(item => item(1).
asInstanceOf[Int] > 140)
println(filteredData)
```
---
```text
Terminal Output
List(List(Bruce Lee, 141), List(Chuck Norris, 170), List(Chuck Liddell, 205))
```
### find
> The find function is very similar to the filter function. However, in the find function, the first item that returns a Boolean of true stops the iteration.
```scala
val data = List(List("Bruce Lee", 141), List("Chuck Norris", 170), List("Chuck Liddell", 205), List("Ronda Rousey", 134))
val findData = data.find(item => item(0).toString.
contains("Chuck"))
println(findData)
```
---
```text
Terminal Output
Some(List(Chuck Norris, 170))
```
### reduce
> It works by reducing a collection of data into a single value by repeatedly applying a binary function to the elements.
```scala
val data = List(List("Bruce Lee", 141), List("Chuck Norris", 170), List("Chuck Liddell", 205), List("Ronda Rousey", 134))
val reducedData = data.map(item => item(1).asInstanceOf[Int]).
reduce(_+_)
println(reducedData)
```
---
```text
Terminal Output
650
```
### fold
> Works exactly like the reduce function except you can seed it with an initial start value
```scala
val data = List(List("Bruce Lee", 141), List("Chuck Norris", 170),List("Chuck Liddell", 205), List("Ronda Rousey", 134))
val foldedData = data.map(item => item(1).asInstanceOf[Int]).
fold(100)(_+_)
println(foldedData)
```
---
```text
Terminal Output
750
```
