# android studio how to
- The setContent() function within the onCreate() function is used to define your layout through composable functions. 
- All functions marked with the @Composable annotation can be called from the setContent() function or from other Composable functions. 
- @Composable function names are capitalized.
- @Composable functions can't return anything.
- To set a different background color for your introduction, you'll need to surround your text with a Surface.
- A Surface is a container that represents a section of UI where you can alter the appearance, such as the background color or border.
- A Modifier is used to augment or decorate a composable.
```
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Surface(color = Color.Cyan) {
        Text(
            text = "Hi, my name is $name!",
            modifier = modifier.padding(24.dp)
        )
    }
}
```
- Annotations can take parameters. Parameters provide extra information to the tools processing them. The following are some examples of the @Preview annotation with and without parameters.
```
@Preview(showBackground=true, showSystemUi=true)
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Surface(color = Color.Cyan) {
        Text(
            text = "Hi, my name is $name!",
            modifier = modifier.padding(24.dp)
        )
    }
}
```
- The Compose function:
-- MUST be a noun: DoneButton()
-- NOT a verb or verb phrase: DrawTextField()
-- NOT a nouned preposition: TextFieldWithLink()
-- NOT an adjective: Bright()
-- NOT an adverb: Outside()

-  the parent UI elements contain children UI elements, which in turn can contain children UI elements
-  The three basic, standard layout elements in Compose are Column, Row, and Box composables.
```
fun GreetingText(message: String, from : String, modifier: Modifier = Modifier) {
    Column {
        Text(
            text = "Hi, " + message + ", happy birthday!",
            fontSize = 100.sp,
            lineHeight = 116.sp,
        )
        Text(
            text = from,
            fontSize = 36.sp,
            lineHeight = 116.sp,
        )
    }
}
```
-  To align in the center of the screen add a parameter called verticalArrangement set it to Arrangement.Center. You will learn more on the verticalArrangement
```
@Composable
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier) {
    Column(
        verticalArrangement = Arrangement.Center,
        modifier = modifier
    ) {
        // ...
    }
}

```
- accessing pictures
```
val image = painterResource(R.drawable.androidparty)
```
