---
title: Composable Functions
parent: JetPack Compose
nav_order: 1
---

## Composable functions ##

Composable functions (composables, controls, components) are special Kotlin functions that emit a user interace. Composable
functions use an annotation `@Composable` unlike regular Kotlin functions.

Typically, you pass data to a composable function, along with set of properties that define how the user interface 
is to be built, behave and appear. 

** Composable functions ** can call other composable functions, typically to define a hierarchy of components.


### Stateless Composables ###

Composables can be grouped into two categories: stateless and stateful.
Composable functions by default are stateless ie. they don't remember or track
data changes.

Example of Stateless composable
```
@Compose
fun Counter(){
    var counter: Int = 0 

    Button(
        modifier = Modifier
            .fillMaxSize()
            .heigh(IntrinsicSize.Min)
            .aspectRatio(2f),
            onClick={
                counter += 1
            }){
                Text(text = "This button has been clicked ${counter} times.")
            }
    )
}

```

Please note that clicking on button doesn't save any state between recompositions of the composable ie. the 
redrawing of the Counter composable.

Turning the above into a stateful compable...

```
 add remember keyword so that values can be tracked and remember across recomposition.

var counter by remember{
    mutableStateOf(0)
}

```

Stateful composable

```

@Composable
fun Counter(){
    
    var counter by remember{
        mutableStateOf(0)
    }

    Button(
        modifier = Modifier
            .fillMaxSize()
            .height(IntrinsicSize.Min)
            .aspectRatio(2f),
        onClick = {
            counter += 1
        }) {
            Text(text = "This button has been clicked ${counter} times.")
        }
}


```