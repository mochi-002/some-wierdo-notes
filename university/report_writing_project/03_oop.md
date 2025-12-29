> Java, the language for which the JVM was developed, is a pure object-oriented programming language that was created by Sun Microsystems in 1995.
# Object-Oriented Programming
- **Object-oriented programming** is a paradigm whose primary purpose is to provide a strategy to deal with **complexity**, as opposed to procedural programming which requires simplicity.
- In the object-oriented paradigm, all aspects of a program use **classes** defined to instantiate **objects**.
- Nothing in traditional object-oriented programming, including programs written in Java, can exist outside of some form of object.
- Objects create **encapsulations** that guard protected variables and provide a namespace for public variables which directly combats namespace collisions. 
- Object-oriented programming takes the capabilities of classes further by introducing the concepts of **inheritance**, **polymorphism**, **interfaces**, and **abstract classes**.
---
- As more data types and methods were added to a program, the dependency complexity for this type of exhaustive checking became exponential, leading to unscalable maintainability problems. 
- In object-oriented programming, in order to tackle this complexity, it was determined that each data type should define the possible methods that can be applied to it within the object itself. 
- The downside to this methodology was that each new data type required the developer to re-implement every single method, which violated the **DRY principle** in scenarios where two data types might share the same implementation of a method. 
- To combat this, object-oriented programming includes the notion of **inheritance**. 
---
## Inheritance
* Just like data types in scala have super-types, classes can also have **superclasses** that they inherit from. This inheritance relationship takes all of the methods and properties of the parent class and gives the child class access to them.
* Thus, two classes who share an implementation of the same method can both access that method without having to write the method twice.
* This inheritance model lends itself really well to modeling simulations of real-world objects. A good example of this is video game simulations.
### Demonstration of inheritance
```java
package CombatGame
class Fighter (var hp: Int = 20) {
    def reduceHP(damage: Int) {
        this.hp -= damage
    }
}

package CombatGame
class Sword (val length: Int = 10, val attackDamage: Int = 5) {
    def attack(opponent: Fighter){
        opponent.reduceHP(attackDamage)
    }
}

package CombatGame
class Knife(override val length: Int = 3, override val attackDamage: Int = 2) extends Sword(length, attackDamage)
```
-  The `extends` keyword defines the inheritance relationship between classes (e.g., `Knife` extends `Sword`).
- The `Knife` class does not need to define `length`, `attackDamage`, or `attack` because it inherits them from `Sword`.
- The `Knife` class provides its own parameter list to override the constructor of the superclass.
- Using `override` before the parameter declarations allows the subclass to set its own default values.
- If no values are provided during instantiation, the defaults are:
    - Knife: `length = 3`, `attackDamage = 2`
    - Sword: `length = 10`, `attackDamage = 5`
- If the subclass (Knife) does not provide a parameter list, it will inherit the superclass defaults (10 and 5).
- Subclasses can add additional properties and methods not present in the parent class.
### Example: Knife can add a new property `healPower` and a method `heal`
```java
package CombatGame

class Knife(
    override val length: Int = 3,
    override val attackDamage: Int = 2,
    val healPower: Int = 5
) extends Sword(length, attackDamage) {
    def heal(ally: Fighter) {
        ally.hp += healPower
    }
}
```
- Methods from a superclass can be overridden by marking them with `override`.
- Overriding is useful when inheriting many methods but changing a few.
- If you find yourself overriding everything, it may be better to write a new class instead of extending.
---
## Polymorphism
- **Polymorphism** literally means “having many forms.”.
- It allows a property of a base type to hold values of any subclass.
- Similarly, a **Fighter** class property of type **Weapon** can hold any subclass of Weapon (e.g., Sword, Knife, Projectile).
- Polymorphism prevents the need to create separate Fighter classes for each weapon type.
### Demonstration of polymorphic inheritance by providing a Weapon type as a property to the Fighter class
```scala
Weapon.scala
package CombatGame
class Weapon (val range: Int, val attackDamage: Int) {
    def attack(opponent: Fighter){
        opponent.reduceHP(attackDamage)
    }
}

Blade.scala
package CombatGame
class Blade (override val range: Int = 2, override val
attackDamage: Int = 5)
    extends Weapon(range, attackDamage)

BroadSword.scala
package CombatGame
class BroadSword(override val range: Int = 3, override val
attackDamage: Int = 6)
    extends Blade(range)

Dagger.scala
package CombatGame
class Dagger(override val range: Int = 1) extends Blade(range)

Fighter.scala
package CombatGame
class Fighter (var weapon: Weapon, var hp: Int = 20) {
    def reduceHP(damage: Int) {
        this.hp -= damage
    }
    def attack(opponent: Fighter){
        weapon.attack(opponent)
    }
}

run.scala
package CombatGame
object run extends App {
    val Thief = new Fighter(new Dagger())
    val Knight = new Fighter(new BroadSword())
    Thief.attack(Knight)
    Knight.attack(Thief)
    println(Thief.hp, Knight.hp)
}    
```
---
![[Pasted image 20251206160113.png]]

---
## Interfaces and Abstract Classes
- Classes like **Weapon**, **Blade**, and **Projectile** can be used for categorization but should not necessarily be instantiated.
- Using the **abstract** keyword prevents a class from being instantiated directly.
- Abstract classes allow you to create a **partial base class** that can be extended to achieve **polymorphism** without fully defining a concrete class.
- A concrete class can only extend **one abstract class**, but an abstract class can contain **abstract methods**.
- Abstract methods define the method name and arguments but do **not** contain implementation; the subclass must implement them.
- If an abstract class contains **only abstract methods** and no constructor, it can be considered an **interface** (traits in scala).
- ---
### Example: Prevent instantiation with abstract

```scala
// Weapon.scala
package CombatGame
abstract class Weapon(val range: Int, val attackDamage: Int) {
    def attack(opponent: Fighter){
        opponent.reduceHP(attackDamage)
    }
}

// Blade.scala
package CombatGame
abstract class Blade(
    override val range: Int = 2,
    override val attackDamage: Int = 5
) extends Weapon(range, attackDamage)

// run.scala
package CombatGame
object run extends App {
    val Thief = new Fighter(new Dagger())
    val Knight = new Fighter(new BroadSword())
    Thief.attack(Knight)
    Knight.attack(Thief)
    println(Thief.hp, Knight.hp)
    new Blade(); // Error: cannot instantiate abstract class
}
```
---
### Example: Abstract method

```scala
// Weapon.scala
package CombatGame
abstract class Weapon(val range: Int, val attackDamage: Int) {
    def attack(opponent: Fighter)
}

// Blade.scala
package CombatGame
abstract class Blade(
    override val range: Int = 2,
    override val attackDamage: Int = 5
) extends Weapon(range, attackDamage) {
    def attack(opponent: Fighter){
        opponent.reduceHP(attackDamage)
    }
}
```
---
### Example: Using a trait as an interface

```scala
// Weapon.scala
package CombatGame
trait Weapon {
    val range: Int
    val attackDamage: Int
    def attack(opponent: Fighter)
}

// Blade.scala
package CombatGame
abstract class Blade(
    override val range: Int = 2,
    override val attackDamage: Int = 5
) extends Weapon {
    def attack(opponent: Fighter){
        opponent.reduceHP(attackDamage)
    }
}
```
---
### Example: Implementing multiple traits

```scala
class Projectile extends Weapon with ArrowTrait with QuiverTrait {
      ... implementation details
}
```
---
### Advantages of OOP
- OOP allows for **organizational and architectural design patterns** to manage the complexity of large codebases.
- It provides a method for **classifying real-world entities** using **interfaces** and **abstract classes** that can be extended.
- **Polymorphism** enables a **rich and customizable type system**, allowing the addition of **generic types** to class properties and static variables.
- OOP provides strategies to **minimize code duplication**.

### Disadvantages of OOP
1. **Verbosity** – OOP code often requires many files and more boilerplate, even for basic examples.    
2. **Upfront planning** – It requires careful architectural considerations before implementation.
	- For **smaller projects**, procedural programming may save time due to its simplicity.
	- A **good compromise** between procedural and object-oriented paradigms can be **functional programming**, if comfortable with its style.