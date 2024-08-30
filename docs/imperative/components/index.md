---
title: Components of an Imperative Android App 
parent: Imperative Progamming in Android Studio
nav_order: 1
---

## Components of Android App

<!-- ![Components of Android App](../mnt/data/image.png) -->

### 0. Gradle

- A tool used to automate the compilation and project build process in Android Studio. Typical workflow involves using Gradle build scripts to download and install third-party libraries and to configure the project.

### 1. Android Lifecycle – Activities/Fragments

- See Imperative Android Lifecycle app (credits Jonathan Nixziol). Please note that JetPack Compose simplifies this
lifecycle in that all lifecycle phases scoped to main composable function.
  
  [LifeCycle Demo](https://github.com/Mbialowas10/Android-LifeCycle-Kotlin)

- **Activity** – just becomes a screen and each activity has 7 methods associated with it.
  1. `onCreate` – gets called when activity is created
  2. `onRestart` – gets called when activity restarts
  3. `onStart` – gets called after activity is created
  4. `onResume` – focus is given back to the app
  5. `onPause` – app is paused, focus is given to another app
  6. `onStop` – app is stopped, focus is given to another app, e.g., answering a phone call
  7. `onDestroy` – app is closed/exited

![Android Lifecycle](img/lifecycle.png)


### 2. The Manifest

- Every project must have a manifest file. What can be found in this file?
  1. Components of app: screens/activities, services, receivers, providers
  2. Permissions
  3. Hardware/software settings
  4. Launch Screen (Activity)

