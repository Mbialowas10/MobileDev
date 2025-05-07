---
title: Firestore Database
parent: Firebase Services
grand_parent: 3rd party Intergrations
layout: home
nav_order: 1
---

## 📘 Firestore Database ##

🔥 What is Firebase Firestore?

A NoSQL cloud database from Firebase that stores data in documents and collections.

- Documents = JSON-like objects (key-value pairs).

- Collections = Containers for documents (like folders).

- Realtime updates: Listen to data changes instantly.

🛠️ Setup in Android Studio

1. Add Firebase to your Android project:

    - Use Firebase Assistant in Android Studio (Tools > Firebase).

    - Follow steps to connect app to Firebase.

2. Add dependencies (in build.gradle):

    ```kotlin
    implementation(platform("com.google.firebase:firebase-bom:32.7.3"))
    implementation("com.google.firebase:firebase-firestore-ktx")
    ```

3. Initialize Firestore:

    ```kotlin
    val db = Firebase.firestore
    ```

📄 Basic CRUD Operations

🟢 Create / Add Data

```kotlin
val user = hashMapOf("name" to "John", "age" to 25)
db.collection("users").add(user)
```

🔵 Read Data
```kotlin
db.collection("users")
    .get()
    .addOnSuccessListener { result ->
        for (document in result) {
            Log.d("Firestore", "${document.id} => ${document.data}")
        }
    }
```

🟡 Update Data

```kotlin
val updates = mapOf("age" to 26)
db.collection("users").document("userId").update(updates)
```

🔴 Delete Data
```kotlin
db.collection("users").document("userId").delete()
```

Useful Concepts

- Document ID: Auto-generated or specified manually.

- Subcollections: Collections inside documents.

- Snapshot Listeners: Observe data in realtime.

```kotlin
db.collection("users").addSnapshotListener { snapshots, e ->
    for (doc in snapshots!!) {
        Log.d("Realtime", "${doc.id} => ${doc.data}")
    }
}
```

Setting some basic security rules
```plaintext
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```