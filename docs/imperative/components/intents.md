---
title: Intents
parent: Imperative Progamming in Android Studio
nav_order: 3
---
Intents – Messaging Object

- Start an activity (a single screen in app)
- Start a service (operation running in background)
- Dispatch a broadcast – a message an app can receive

### Using Intents:

- To make use of Intent on originating source code screen, add the following:

```kotlin
btnResult.setOnClickListener(){
    val intent = Intent(this, TargetActivity::class.java)
    startActivity(intent)
}
```

- Note this typically goes inside an event handler for processing. In summary, you create an intent object then pass this object to `startActivity`.

#### Passing Data Between Screens:

- Wait… what if you want to pass data from one screen to the next?
  Add a call to `putExtra` method:

```kotlin
val btnResult:Boolean = findViewById(R.id.btnGoToNextScreen)
btnResult.setOnClickListener(){
    // intent - goto Next Screen
    var intent:Intent(this, ResultActivity::class.java)

    intent.putExtra("key", value)
    startActivity(intent)
}

```

- Then on `destinationScreen` (endpoint), a bundle object is created to retrieve the data:

```kotlin
class ResultActivity : AppCompatActivity(){

    override fun onCreate(savedInstanceState: Bundle?){
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_result)

        // receive data
        val bundle:Bundle? intent.extras
        val name: Any? = bundle?.get(name)
        var tvResult: TextView? = null

        tvResult = findViewById<TextView>(R.id.tvResult)
        tvResult.text = "Congratulations ${name.toString(), you made it to your destination!"}

        Toast.makeText(this, "Your name is ${name.toString()}", Toast.LENGTH_LONG).show()
    }
}
```

- Here we made use of Intent object to pass control over to a new screen. We can do the same with passing control over to a different app within the Android suite of programs.

```
 // 2. Intent - redirect user to another app e.g. a web page
 val btnCNN: Button = findViewById(R.id.btnCNN)

 btnCNN.setOncClickListener(){
    intent = Intent(Intent.ACTION_VIEW)
    intent.setData(Uri.parse(https://cnn.com))
    startActivity(intent)
 }
```
--- 

