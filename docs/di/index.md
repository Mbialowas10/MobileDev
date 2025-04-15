---
title: Dependency Injection (DI) in JetPack Compose
has_children: false
nav_order: 6
---


# What is Dependency Injection?

Dependency Injection, DI for short is a software design pattern that is closely
related to Composition. Ie. an object receives its dependencies (usually in form
of other objects or composable functions in JetPack Compose) rather they creating 
these internally.

Some benefits to using this approach include:
1. loose coupling,
2. making code more modular and resuable
3. testable
4. maintainable

We have been been using Composition more than Inheritance since we moved to 
declarative programming with JetPack Compose. Ie. we typically pass data downwards 
uniformly through our app and events bubble upwards. For example, please consider the 
simply manual process for DI below.

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

class V8Engine : Engine {
    override fun type() = "V8 Engine"
}

class AutomaticTransmission : Transmission {
    override fun type() = "Automatic"
}

class MichelinTires : Tires {
    override fun brand() = "Michelin"
}

```
**Note:** The use of intefaces for general types: Engine, Transmission, Tires and their respective concrete classes: V8Engine, AutomaticTransmission, and MichelinTires


Note setup a car that uses these component objects.
```kotlin
class Car(
    private val engine: Engine,
    private val transmission: Transmission,
    private val tires: Tires
) {
    fun specs(): String {
        return "Car with ${engine.type()}, ${transmission.type()}, and ${tires.brand()} tires."
    }
}
```

Time to make a contain to instantiate these object types
```kotlin
class CarContainer {
    private val engine: Engine = V8Engine()
    private val transmission: Transmission = AutomaticTransmission()
    private val tires: Tires = MichelinTires()

    val car: Car = Car(engine, transmission, tires)
}

```

Integrate into JetPack Compose
```kotlin
@Composable
fun CarScreen(car: Car) {
    val specs = remember { car.specs() }
    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp)
    ) {
        Text("Car Specs", style = MaterialTheme.typography.headlineMedium)
        Spacer(Modifier.height(12.dp))
        Text(specs)
    }
}
```

Call it from MainActivity
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val container = CarContainer() // manual DI

        setContent {
            MaterialTheme {
                CarScreen(car = container.car)
            }
        }
    }
}
```
A few items to note about manual DI:
1. Manual creation of dependencies (no @Inject, no Hilt)
2. You manage how app is connected






