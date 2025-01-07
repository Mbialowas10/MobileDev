---
title: Functions
parent: Kotlin
nav_order: 3
---

# Functions

Functions are `fun`! Sometimes they consume values and sometimes they return values
to the caller. If functions do not return a value then its return type is `Unit`. This 
is is similar to the word `void` for those familar with Java programming Language.

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

## Lambda Expressions

Let's pretent we want to lowercase all characters in a string. This could be useful
if we want to standarize form input.
```kotlin
fun lowerCaseInput(text:String): String {
    return text.lowercase()
}

fun main(){
    print(lowerCaseInput("Greetings!"))
}
```
We could write this more in an alternative format to make it more readable.

```kotlin
    fun main(){
        val lowerCaseInput = { text: String -> text.lowercase() }
        print( lowerCaseInput("Greetings") )
    }
```

```plaintext
text:String represents the parameter
function body appears after arrowhead ->
```
**Note** no return keyword used here

Lambda expressions are used alot in JetPack Compose as we will learn later in the course.

Consider the lambda usage below to transform a set of values from integers to strings.

```kotlin
fun main() {
    // Input list of grades
    val grades = listOf(2.0, 2.5, 3.0, 3.5, 4.0, 4.5)

    // Mapping numeric grades to letter grades
    val letterGrades = grades.map { grade ->
        when (grade) {
            2.0 -> "C"
            2.5 -> "C+"
            3.0 -> "B"
            3.5 -> "B+"
            4.0 -> "A"
            4.5 -> "A+"
            else -> "Unknown" // Handle unexpected values
        }
    }

    // Print the resulting letter grades
    println(letterGrades) // Output: [C, C+, B, B+, A, A+]
}
```

## Anonymous Functions 
Functions without a name

```kotlin
fun sumNumbers(vararg numbers: Int): Int {
    return numbers.sum()
}

fun main() {
    // Example usage
    val result1 = sumNumbers(1, 3, 5)
    val result2 = sumNumbers(4, 5, 6, 7)

    println("Sum 1: $result1") // Output: Sum 1: 9
    println("Sum 2: $result2") // Output: Sum 2: 22
}
```
**Note** use of vararg keyword can take any number of arguments

