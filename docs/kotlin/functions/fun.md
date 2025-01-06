---
title: Functions
parent: Kotlin
nav_order: 3
---

# Functions

Functions are `fun`! Sometimes they consume values and sometimes they return values
to the caller.

## Fx Declaration
```kotlin
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
**Note:** a and b are referred to as named arguments ie. you can pass values to function
as named arguements
```kotlin
    println(newAndImprovedAddNumbersV2(a=1,b=3)
```
The benefit to using named arguments that you don't have to pass arguments in a specific order.
```kotlin
    println(newAndImprovedAddNumbersV2(b=3,a=1)
```

## Default paramater values
```kotlin
    fun printArg(name:String = "N/A"){
        println("Hello ${name}")
    }

    fun main() {
        printArg("Mike")    // Hello Mike
        printArg()          // Hello N/A
    }
```

## Invoking a function
```kotlin
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