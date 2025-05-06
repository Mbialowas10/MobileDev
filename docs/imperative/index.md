---
title: Imperative Progamming in Android Studio
layout: home
has_children: true
nav_order: 3
---

## Imperative (Traditional) Android Development

### Views
![Views Image](img/views.png)
- A piece of UI, think of it as a box.
- For more, please see [Android Views Documentation](https://developer.android.com/develop/ui/views/layout/declaring-layout).
- A view serves as the base class for UI components.

### ViewGroup
- Can hold 0 or more views; think of `ViewGroup` as a Layout.
- Example views:
  - `TextView`
  - `ImageView`
  - `Button`
  - `EditText`
  - `ListView`
  
### Identifying Views
- All views should have a unique identifier (id) so the UI can be bound to code. This allows developers to write code
that interacts with controls allowing control UI behaviour to be changed.
  
```xml
<Text android:id="@+id/mytext"/>
```

### Binding Layout to Code
- You can bind this layout to your Kotlin/Java code as follows:
  
```kotlin
val label: TextView = findViewById(R.id.mytext)
```

### Attributes
- Views have attribute (properties) similar to CSS used in web development.

### Demonstration of Widgets
- For demonstration of widgets, please see:
  - [widgetsDemo on GitHub](https://github.com/Mbialowas10/widgetsDemo)
  - For more on Imperative UI common components, see [Imperative Common UI components](https://github.com/Mbialowas10/Common_UI_Components.git) link.
  - For JetPack Compose equivlent, see [JetPack Compose Common UI components](https://github.com/Mbialowas10/Common_UI_Components_JetPack_Compose.git).

