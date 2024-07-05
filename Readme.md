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
- conditionals
```
fun main() {
    println(1 == 1)
}
```
- when statement
```
fun main() {
    val trafficLightColor = "Black"

    when (trafficLightColor) {
        "Red" -> println("Stop")
        "Yellow" -> println("Slow")
    }
}
```
- result of if/else statement can be stored in a variable
```
fun main() {
    val trafficLightColor = "Black"

    val message = 
      if (trafficLightColor == "Red") "Stop"
      else if (trafficLightColor == "Yellow") "Slow"
      else if (trafficLightColor == "Green") "Go"
      else "Invalid traffic-light color"

    println(message)
}
```
# Use nullable variables
- val favoriteActor = null
- In Kotlin, there's a distinction between nullable and non-nullable types: Nullable types are variables that can hold null. Non-null types are variables that can't hold null.
- nullable type, compilation error because access to potentially null object
```
  fun main() {
    var favoriteActor: String? = "Sandra Oh"
    println(favoriteActor.length)
}
```
- You can use the ?. safe call operator to access methods or properties of nullable variables.
```
fun main() {
    var favoriteActor: String? = "Sandra Oh"
    println(favoriteActor?.length)
}
```
- You can also use the !! not-null assertion operator to access methods or properties of nullable variables.
```
fun main() {
    var favoriteActor: String? = "Sandra Oh"
    println(favoriteActor!!.length)
}
// or
fun main() {
    var favoriteActor: String? = null
    println(favoriteActor!!.length)
}
```
- The ?: Elvis operator is an operator that you can use together with the ?. safe-call operator. With the ?: Elvis operator, you can add a default value when the ?. safe-call operator returns null.
```
fun main() {
    var favoriteActor: String? = "Sandra Oh"

    val lengthOfName = favoriteActor?.length ?: 0

    println("The number of characters in your favorite actor's name is $lengthOfName.")
}
```
- kotlin oop
```
class SmartDevice constructor() {
    ...
}
...
class SmartDevice(val name: String, val category: String) {
    var deviceStatus = "online"

    constructor(name: String, category: String, statusCode: Int) : this(name, category) {
        deviceStatus = when (statusCode) {
            0 -> "offline"
            1 -> "online"
            else -> "unknown"
        }
    }
    ...
}
```
- In the SmartDevice superclass, add an open keyword before the class keyword to make it extendable:
```
open class SmartDevice(val name: String, val category: String) {
    ...
}
```
- inheritence
```
class SmartTvDevice(deviceName: String, deviceCategory: String) :
    SmartDevice(name = deviceName, category = deviceCategory) {
}
```
- In a HAS-A relationship, an object can own an instance of another class without actually being an instance of that class itself.
- an IS-A relationship between the SmartDevice superclass and SmartTvDevice subclass, it means that whatever the SmartDevice superclass can do, the SmartTvDevice subclass can do
- override
```
class SmartLightDevice(deviceName: String, deviceCategory: String) :
    SmartDevice(name = deviceName, category = deviceCategory) {
...

    override fun turnOff() {
        deviceStatus = "off"
        brightnessLevel = 0
        println("Smart Light turned off")
    }
}
```
