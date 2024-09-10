---
title: Compose Examples
parent: JetPack Compose
nav_order: 2
---

```
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            ComposeIntroductionTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                    Column(){
                        val scrollState = rememberScrollState()
                        Counter(modifier = Modifier.padding(innerPadding))
                        // call another composable
                        Switcher()

                        // custom List
                        //CustomList()

                        // call custom grid
                        CustomGrid()
                    }

                }
            }
        }
    }
}

@Composable
fun Counter(modifier: Modifier = Modifier){

    var counter by remember{
        mutableStateOf(0)
    }

    Button(
        modifier = modifier,
        onClick = {
            counter += 1
        }){
            Text(text = "This button has been clicked $counter times.")
        }
}

// another compose function
@Composable
fun Switcher(){
    val checked = remember { mutableStateOf(false) }

    Column{
        Switch(
            checked = checked.value,
            onCheckedChange = { checked.value = it }
        )
        if(checked.value){
            Text("Switch is checked")
        }else{
            Text("Switch is not checked")
        }
    }
}

// CustomList
@Composable
fun CustomList(){


    val itemsList = List(20000) { "Control $it" }

    LazyColumn {
        items(itemsList) { item ->
            Text(text = item)
        }
    }
}

// custom grid
@Composable
fun CustomGrid(){
    // Sample data for the grid
    val itemsList = List(50) { "Control $it" }

    LazyVerticalGrid(
        columns = GridCells.Fixed(5),  // 5 columns in the grid
        modifier = Modifier.fillMaxSize()
    ) {
        items(itemsList) { item ->
            GridItem(itemText = item)
        }
    }
}
@Composable
fun GridItem(itemText: String) {
    Box(
        modifier = Modifier
            .size(100.dp)
            .background(Color.Cyan),
        contentAlignment = Alignment.Center
    ) {
        Text(
            text = itemText,
            fontSize = 20.sp,
            fontWeight = FontWeight.Bold
        )
    }
}






```