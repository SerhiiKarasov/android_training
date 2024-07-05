# android studio how to, building first app
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
- to adjust the scale type of the image, which says how to size the image, to make it fullscreen.

There are quite a few ContentScale types available. You use the ContentScale.Crop parameter scaling, which scales the image uniformly to maintain the aspect ratio so that the width and height of the image are equal to, or larger than, the corresponding dimension of the screen.
- To set children's position within a Row, set the horizontalArrangement and verticalAlignment arguments.
- For a Column, set the verticalArrangement and horizontalAlignment arguments.
- For each side of the composable, the padding modifier takes an optional argument that defines the amount of padding.

```
Modifier.padding(
    start = 16.dp,
    top = 16.dp,
    end = 16.dp,
    bottom = 16.dp
)
```
- color with the Color class and the color hex code (a hexadecimal way to represent a color in RGB format
```
Text("Example", color = Color(0xFF3ddc84))
```
- You can also use Spacer composable to make spacing more explicit.
- TalkBack is the Google screen reader included on Android devices. TalkBack gives you eyes-free control of your device.
- TalkBack uses the contentDescription parameter to help with the accessibility of the app. If the Image composable is only used for decorative purposes or there's a Text element that describes the Image composable, you can set the contentDescription parameter to null.
- You can use the Icon composable to add icons from Material Design. You can change the Tint parameter to adjust the icon color to fit the style of your business card.
- You can experiment with various values of fontSize, textAlign, color, and fontWeight parameters to style your text.

# kotlin basics
- lambda
```
val helloPrint = {
    println("Hi!")
}
someOtherFunction(helloPrint)
someOtherFunction({println("Hi!")})
```
