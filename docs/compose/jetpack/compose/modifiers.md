---
title: Modifiers 
parent: JetPack Compose
nav_order: 5
---

## Modifiers ##

Modifiers allow compoosbles to be configured so that 
their presenation can change ie. the way they look on screen.
The modifier can be thought of like a css selector that can styles
applied to it. Modiifiers are tyopically more generic in nature in
that they are settings/styles that can be applied to Composable, different 
from passsing parameters to a composable that are specific to that compose.

Modifier is a built-in Compose object designed to store config settings for a 
composable. Things that typically can be set in modifier object include but not limited to things
such as borders, padding, background, event handlers.

 To create a new blank modifier.

 `val modifier = Modifier`

to create a new modifier that has padding set to 5.dp around a composable use:
`val modifier = Modifier.padding(all=5.dp)`

operations can be chained together to change even more appearance characteristics of 
a composable.

```kotlin
val modifier = Modifier
                .border(width = 5.dp, color= Color.Blue)
                .padding(all = 5.dp)
```

**Please Note** that order matters when chaining method calls togeher, example above is not the same 
as 

```kotlin
val modifier = Modifier
                .padding(all = 5.dp)
                .border(width = 5.dp, color= Color.Blue)
                
```
