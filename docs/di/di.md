---
title: Dependency Injection (DI) using Hilt
has_children: false
parent: Dependency Injection (DI) in JetPack Compose
nav_order: 1
---

## Dependency Injection (DI) using Hilt 

1. Add Hilt dependencies to build.gradle (app)

```kotlin
plugins {
    id("com.android.application")
    id("kotlin-kapt")
    id("dagger.hilt.android.plugin")
}

dependencies {
    implementation "com.google.dagger:hilt-android:2.50"
    kapt "com.google.dagger:hilt-android-compiler:2.50"

    // Compose ViewModel integration
    implementation "androidx.hilt:hilt-navigation-compose:1.2.0"
}
```

and in build.gradle (project) file
```kotlin
buildscript {
    dependencies {
        classpath "com.google.dagger:hilt-android-gradle-plugin:2.50"
    }
}
```

2. Create Interfaces and implementations - same as before

```kotlin
interface Engine {
    fun type(): String
}

interface Transmission {
    fun type(): String
}

interface Tires {
    fun brand(): String
}

class V8Engine @Inject constructor() : Engine {
    override fun type() = "V8 Engine"
}

class AutomaticTransmission @Inject constructor() : Transmission {
    override fun type() = "Automatic"
}

class MichelinTires @Inject constructor() : Tires {
    override fun brand() = "Michelin"
}
```

Car class 

```kotlin
class Car @Inject constructor(
    private val engine: Engine,
    private val transmission: Transmission,
    private val tires: Tires
) {
    fun specs(): String {
        return "Car with ${engine.type()}, ${transmission.type()}, and ${tires.brand()} tires."
    }
}
```

4. Hilt module to bind dependencies
```kotlin
@Module
@InstallIn(SingletonComponent::class)
abstract class CarModule {

    @Binds
    abstract fun bindEngine(engine: V8Engine): Engine

    @Binds
    abstract fun bindTransmission(transmission: AutomaticTransmission): Transmission

    @Binds
    abstract fun bindTires(tires: MichelinTires): Tires
}
```

5. Inject Car into viewModel

```kotlin
@HiltViewModel
class CarViewModel @Inject constructor(
    private val car: Car
) : ViewModel() {
    fun getSpecs(): String = car.specs()
}
```

6. Create a Composable
```kotlin
@Composable
fun CarScreen(viewModel: CarViewModel = hiltViewModel()) {
    val specs = remember { viewModel.getSpecs() }

    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp)
    ) {
        Text("Car Specs", style = MaterialTheme.typography.headlineMedium)
        Spacer(modifier = Modifier.height(12.dp))
        Text(specs)
    }
}
```

7. App setup for Hilt

```kotlin
@HiltAndroidApp
class CarApp : Application()
```

8. Register app in Mainifest.xml

```kotlin
<application
    android:name=".CarApp"
    ... >
```
9. Run code from MainActivity

```kotlin
@AndroidEntryPoint
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContent {
            MaterialTheme {
                CarScreen()
            }
        }
    }
}
```
**Notes: 
1. Object are note created manually
2. Dependepencies are injected automatically using @Inject annotation
3. App layers: ViewModels, respositories, and services are decoupled makeing them easy to test.