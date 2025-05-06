---
title: Conciseness 
parent: Kotlin
nav_order: 1
---

## Concise Lanaguage - less is more ##

Kotlin lets you work with immutable and mutable variables (read-only and writable variable types). To make a variable
read only use val and to make a variable writable use var. Kotlin recommends
using **val** over **var** whenever possible. This often is a convention
used in functional programming.

```kotlin
val PI = 3.1452 - constant as read-only
var variable = 10.0 - a typical variable ie. its value can change over time

```

### 1. Type inference ###

Kotlin allows for type inference. The Kotlin complier is able to determine 
datatype from assigned value. **Please note that the expression below involving
avogadro's number are equivalent**


```kotlin
val avogadroNumber = 6.022e23
val avogadroNumber:Double = 6.022e23

```

_Recommendation here is to declare all variable types_

```kotlin
val str = "Hello Class"
println(str)
println(str.javaClass)
```
```kotlin
val num = 10
println(num)
println(num.javaClass)
```

If you wanted to do this explicity, would could do...

```kotlin
val str:String = "Hello Class"
println(str)
println(str.javaClass)
```

```kotlin
val num:Int = 10
println(num)
println(num.javaClass)
```

#### 1. Main Function ####

 In order to run a Kotlin program, code needs to be placed inside of a main function, similar to other 
 environments. Comments are ignored by the Kotlin interpreter.

```kotlin
    fun main() {
        runSomeFunction()
    }
```
#### 2. Comments ####
```kotlin
    // single line comment

    /*
        multiline comment 
    */ 

    /**
      * Purpose: kDoc - used for code documentation
      * @param x: int 
      * @param y: int
      * @return sum: int
      * @throws exception 
      */
```


#### 2. Semicolons not required ####
**Note: runSomeFunction() above does not have a semi-colon ending it. It is typically to omit 
the use of semi-colos after expresssions.
```kotlin
10 * 5
```


#### 2. Classes are Optional ####

You can call a function without having it live within a Class (kinda like calling a static method). How cool is that? To do this, just create a kotlin file (file extension should be .kt) and add any number of functions to it. In this way the file acts kind of like a module.

```kotlin
fun greetings(){
  println("Hello Class")
}

greetings()
```

Please note all kotlin functions have `fun` keyword followed by `name of function`