---
title: Less
parent: Kotlin
nav_order: 1
---

### Concise Lanaguage - less is more ###

#### 1. Semicolons not required ####

```
10 * 5
```

#### 2. Type inference ####
what does this mean? type can be inferred by value not data type

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

You can call a function without having it live within a Class (static method) or an instance of an object. How cool is that?

```
fun greetings(){
  println("Hello Class")
}

greetings()
```