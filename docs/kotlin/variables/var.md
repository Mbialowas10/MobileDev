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


   