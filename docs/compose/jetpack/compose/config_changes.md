---
title: Configuration changes
parent: JetPack Compose
nav_order: 4
---

## State and configuration changes

What happens when you rotate your emulator?

![Emulator](img/emulator.png)

The state is lost ie. it is not remembered

![Emulator lost state](img/statelost.png)

Recall the `remember` keyword is used to remember the state(date) between 
recompositions of a composable. To save state between configuration changes
use `rememberSavable`. When this keyword is utilzed, state will be saved not
only through recomposition but through configuration changes.

