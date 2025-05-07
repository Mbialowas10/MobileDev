---
title: Firebase Authentication
parent: Firebase Services
grand_parent: 3rd party Intergrations
layout: home
nav_order: 2
---

## Firebase Authentication ##

🔑 What Is Firebase Authentication?

Firebase Authentication is a service that provides backend services, easy-to-use SDKs, and UI libraries to authenticate users to your app. 

It supports:

- Email/password login
- Phone number authentication
- Federated identity providers like Google, Facebook, Twitter, GitHub, Apple, etc.

🔧 Setting Up Firebase Auth in Android Studio

1. Add Firebase to your Android project:

    - Go to Firebase Console
    - Create a new project or use an existing one
    - Register your Android app (package name must match)
    - Download google-services.json and place it in app/ folder

2. Update Gradle Files:

In project-level build.gradle:

```kotlin
// Top-level build file - inside build.gradle.kts project file
buildscript {
    dependencies {
        classpath("com.google.gms:google-services:4.4.1") // or latest version
    }
}
```

Alternatively, just add these dependencies in Android Studio -> Tools -> Firebase -> Firestore

👤 Email and Password Authentication
```kotlin
FirebaseAuth.getInstance().createUserWithEmailAndPassword(email, password)
    .addOnCompleteListener { task ->
        if (task.isSuccessful) {
            val user = FirebaseAuth.getInstance().currentUser
            // Navigate to home screen or show success
        } else {
            // Show error message
        }
    }

```
👤 Sign In With Email and Password

```kotlin
FirebaseAuth.getInstance().signInWithEmailAndPassword(email, password)
    .addOnCompleteListener { task ->
        if (task.isSuccessful) {
            // Login success
        } else {
            // Login failure
        }
    }
```

🔄 Managing Authentication State

```kotlin
val auth = FirebaseAuth.getInstance()
val currentUser = auth.currentUser

if (currentUser != null) {
    // User is signed in
} else {
    // No user is signed in
}

```

🚪 Sign Out

```kotlin
FirebaseAuth.getInstance().signOut()

```
**Note:** Firebase provides these additional features:
- Email verification
- Password reset
- Multi-factor authentication