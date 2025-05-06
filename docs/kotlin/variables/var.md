---
title: Datatypes
parent: Kotlin
nav_order: 2
---

### 1. Datatypes

Similar to other programming languages, the notion of Primitive and Non-Primitive dataTypes exist.

Primitives are non-object types.

    Primitive
        -Integer, Double, Character, Boolean
    Non-Primitive
        -String, Array Classes


### 2. Strings

Strings can be printed out like in other languages by calling the println method 
`println()`

```kotlin
    var game_title:String
    game_title = "Super Mario Wonder"

    println(game_title)
```

String intrapolation can also be used to print out values of variables

```kotlin
  println("Nintendo Switch came about with ${game_title})  
```

_note the use of ${} to surround the variable_

What if you need to print multiplelines?

Kotlin has a nice solution for this.

```kotlin
    fun main() {
        val multiLineString = """
            This is line 1
            This is line 2
            This is line 3
        """
        println(multiLineString)
}

```




### 3. Other Data Types
```plaintext
Category                |       Basic types               |               Example code
-----------------------------------------------------------------------------------------
Integers                |   Byte, Short, Int, Long        |         val month: Int = 01
Unsigned integers       |   UByte, UShort, UInt, ULong    |         val points: UInt = 500u
Floating-point numbers  |   Float, Double                 |         val currentTemp: Float = 25.0f, val price: Double = 99.99
Booleans                |   Boolean                       |         val isEnabled: Boolean = true
Characters              |   Char                          |         val separator: Char = '-'
Strings                 |   String                        |         val month: String = "January"
```

### 4. Collections
```plaintext
Type   |    Description                         | Example
------------------------------------------------------------------------------------------------------------------------------------------------------------
List   |    ordered collection of items         |   // read only list 
                                                    val readOnlyVehicles = listOf("Ferreri", "Corvette","Mustang")
                                                    println(readOnlyVehicles)
Sets   |    unique unordered collection of items|   // mutable lists
                                                    // Mutable list with explicit type declaration
                                                    val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
Maps   |    key-value pairs                     |   // Read-only set
                                                    val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
                                                    // Mutable set with explicit type declaration
                                                    val fruit: MutableSet<String> = mutableSetOf("apple", "banana")
```




   