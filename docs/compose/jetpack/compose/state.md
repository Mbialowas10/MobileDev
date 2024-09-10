---
title: State
parent: JetPack Compose
nav_order: 3
---

## State, Recomposition, Data flow and State Hoisting

Compose is known as a declarative language and as such it is a different 
programming paradigm used in software development. 

Recall that Imperative (Traditional) differs from Declarative Programming 
in the way control flow and logic is handled within the application.

Examples of Delarative languages include: SQL, HTML, CSS, Haskell, React, 
and JetPack Compose this differs from C, C++, Java, and Assembly (Imperative types).

In declarative type you tell the computer what you want to see or do and the computer 
determines how best to carry out task on your behalf. Imperative approach follows more 
of stepy by step procedure and explicit instructor for how best to carry out an action 
(algorithm).

Back to our discussion now of using a declarative language: Compose. 

### State

State can be thought of as application data that changes over time. Please don't confuse 
this with data contained in a variable. Compose uses a special type of variable to track 
its state. We use the keyword `remember` in compose to remember the value of data between 
recompositions (redrawings of a control) in jetPack compose. This is different behaviour 
from re-initializing a variable each time a function is called.

The common design patter employed in Compose is that of creating hierarchies out of composable 
functions. Recall that a composable function is a special function denoted with an annotation 
`@composable` and that when this function gets run it emits a new piece of UI. Moreover, we 
generate new screens in compose from nesting controls (composables) within other controls (composables). 
And when data changes, a new UI is emitted or redrawn on screen. This differs greatly from having
to manage state on your own say the way you would when doing imperative programming e.g.
`etInput = this.setText("A new piece of data passed")`

Recomposition is when the data changes in a the hierarchies of composable functions. The cool part 
here is the as soon as Compose detects a state change (data changed) it is process in composable functions
that use this date in unidrectional flow. Data flows from parent to child contol (composable) and events bubble
upwards from child to parent when invoked. The entire UI tree is not recomposed with the state changes, only the composables
that read the data will need to be recomposed (redrawn to screen) making this operation itelligent by design.








