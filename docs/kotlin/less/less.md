---
title: Less
parent: Kotlin
nav_order: 1
---

### Concise Lanaguage - less is more ###

Kotlin lets you work with read-only and mutable variables. To make a variable
read only use val and to make a variable writable use var. Kotlin recommends
using **val** over **var** whenever possible. Perhaps, this becomes more important
when performing functional programming.

```
val pi = 3.1452 - constant as read-only
var variable = 10.0 - a variable

```







#### 1. Semicolons not required ####

```
10 * 5
```

#### 2. Type inference ####
Kotlin allows for type inference. The Kotlin interpreter is able to determine 
datatype based upon value assigned to variable. Please note 
**both expresssions below are equivalent**

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

#### 3. Classes are Optional ####

You can call a function without having it live within a Class (kinda like calling a static method). How cool is that?

```
fun greetings(){
  println("Hello Class")
}

greetings()
```

Please note all kotlin functions have `fun` keyword followed by `name of function`