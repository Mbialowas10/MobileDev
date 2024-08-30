---
title: Functions
parent: Kotlin
nav_order: 3
---

# Functions

Functions are `fun`! Sometimes they consume values and sometimes they return values
to the caller.

## Fx Declaration
```
// note this function is not consuming any values, but it is returning an Int
fun addNumbers():Int{
    return 80+6
}
// semi-colons are optional
fun newAndImprovedAddNumbers(a:Int, b:Int):Int{
    return a + b
}

// short-hand notation when returning values
fun newAndImprovedAddNumbersV2(a:Int, b:Int) = (a+b)
```

## Invoking a function
```
fun main(){
    print("Hello I'm a function without an newline")
    println()
    println(addNumbers())
    println(newAndImprovedAddNumbers(5,15))
    println(newAndImprovedAddNumbersV2(2,3))
}
```

Output
```
Hello I'm a function without an newline
86
20
5
```