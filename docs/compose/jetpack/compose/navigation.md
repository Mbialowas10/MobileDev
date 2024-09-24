---
title: Navigation 
parent: JetPack Compose
nav_order: 7
---

## Navigation in JetPack Compose ##

Navigating in JetPack Compose involves the use of `NavController` and `NavHost`.
NavController is responsible for managing routing information within composables 
in a mobile app. It even has a `navigate` function that can be called on it.
NavController also manages a Stack often referred to as the BackStack. It operates as 
a typical stack data structure would work. As screens (composables) are interacted with they 
are in turn added to the stack. They follow the First in last out principle.

![Stack Data Structure](img/stack.png)

Additionally, in order to use navigation within your Android app. You must add the dependency to the 
project.


libs.versions.toml
```kotlin
[versions]
    navigationCompose = "2.8.0"

[libraries]
    androidx-navigation-compose = { group = "androidx.navigation", name = "navigation-compose", version.ref = "navigationCompose" }
```
build.gradle.kts(Module :app)

```kotlin
    implementation(libs.androidx.navigation.compose)
```

### Destination Object Class Type for managing routes ###
A common practice is to create a Destination class of Type object to manage routing information.
```kotlin
    sealed class Destination(val route: String){
    object Movie: Destination("movie")

    object  Search: Destination("search")
    object Watch: Destination("watch")
    object MovieDetail: Destination("movieDetail/{movieID}"){
        fun createRoute(movieID: Int?) = "movieDetail/$movieID"
    }
}
```

### Using NavController and NavHost to Invoke Composable ###
NavController is passed to NavHost to manage routing information. A
corresponding composable gets emitted when this route loads.

```kotlin
    val navController = rememberNavController()

    NavHost(navController = navController as NavHostController, startDestination = Destination.Movie.route ){
            composable(Destination.Movie.route){
                MovieScreen()
            }
            composable(Destination.Search.route){
                SearchScreen()
            }
            composable(Destination.Watch.route) {
                WatchScreen()
            }
            composable(Destination.MovieDetail.route){ navBackStackEntry ->
                MovieDetailScreen()
            }
```
Here we can see that depending on which route gets passed to composable we load in a different composable (screen)