---
title: Conciseness 
parent: Kotlin
nav_order: 1
---

## Concise Lanaguage - less is more ##

Kotlin lets you work with read-only and write variables. To make a variable
read only use val and to make a variable writable use var. Kotlin recommends
using **val** over **var** whenever possible. This often is a convention
in functional programming.

```
val pi = 3.1452 - constant as read-only
var variable = 10.0 - a typical variable ie. its value can change over time

```

### 1. Type inference ###

Kotlin allows for type inference. The Kotlin complier is able to determine 
datatype from assigned value. **Please note that the expression below involving
avogadro's number are equivalent**


```
val avogadroNumber = 6.022e23
val avogadroNumber:Double = 6.022e23

```

_Recommendation here is to declare all variable types_

```
val str = "Hello Class"
println(str)
println(str.javaClass)
```
```
val num = 10
println(num)
println(num.javaClass)
```

If you wanted to do this explicity, would could do...

```
val str:String = "Hello Class"
println(str)
println(str.javaClass)
```

```
val num:Int = 10
println(num)
println(num.javaClass)
```

#### 1. Main Function ####

 In order to run a Kotlin program code needs to be placed inside of a main function, similar to other 
 environments. Comments are ignored by the Kotlin interpreter.

```
    fun main() {
        runSomeFunction()
    }
```
#### 2. Comments ####
```
    // single line comment

    /*
        multiline comment 
    */ 
```


#### 2. Semicolons not required ####
**Note: runSomeFunction() does not have a semi-colon ending it
```
10 * 5
```


#### 2. Classes are Optional ####

You can call a function without having it live within a Class (kinda like calling a static method). How cool is that?

```
fun greetings(){
  println("Hello Class")
}

greetings()
```

Please note all kotlin functions have `fun` keyword followed by `name of function`