Code structure of the MainActivity.kt file
````kotlin
     class MainActivity : ComponentActivity() {
        override fun onCreate(savedInstanceState: Bundle?) {
            super.onCreate(savedInstanceState)
            setContent {
                MyApp {
                		Surface(modifier = Modifier.fillMaxSize(), color = MaterialTheme.colorScheme.background){
                			Greeting()
                		}
                }
            }
        }
    }
````

Summary of the code:
````Kotlin
    class MainActivity : ComponentActivity(){}
````
The ``ComponentActivity()`` is a class provided by `AndoidX`, designed to simplify the creation of UI components  and manage their lifecycle.

````kotlin
    overrid fun onCreate() {}
````
The  `override` replace the default implementation of the method `onCreate()` this is because the polymorphism(remember Oriented Object Programming).

The ``OnCreate()`` is a lifecycle callback method, it is called when an *activity* is created.

`savedInstanceState: Bundle?`
The  parameter ``savedInstanceState`` is a reference to a class `Bundle` that allows you store a set of key-value pairs of various data types, such as `String`, `int, `boolean` ...

`?` That indicates that teh parameter can be *nullable*, meaning it can have a value or be *null*

```savedInstanceState``` is used to *restore* the activity's state after is destroyed by the system, such as when the device is rotated or the app is killed.
the ``savedInstanceState`` contains the data that was saved in the `onSaveInstanceState()` method, which is called before the activity is destroyed.

NOTE:
*If the activity is created for the first time, ``savedInstancedState`` is `null`.*

*If the activity is re-created after being destroyed, `savedInstanceState` is `not null` and contains the saved data.*

````kotlin
    super.onCreate(savedInstanceState)
````
The ``super`` keyword is used to refer to the members of the parent class. The `MainActivity` class *inherits* from the `ComponentActivity` class, which means `MainActivity` can access its properties and methods of the `ComponentActivity`.
The ``super`` keyword allows you to call the `onCreate()` method of the `ComponentActivity` clas from the `onCreate()` method of the `MainActivity` class.


The ``onCreate()`` method is one of the lifecycle methods of an Android activity, which is responsible for initializing the user interface  and setting up the activity.

By calling `super.onCreate(savedInstanceState)`, remember The `savedInstanceState` is a `Bundle` object that contains the saved state od the activity, such as the values of some views or variables, you are telling the Android framework to run the code in the `onCreate()` method of the `ComponentActivity` class, which handles some essential some essential tasks such as creating the window, setting the content view, and restoring the saved state. 
NOTE: If you omit this line, the ``onCreate()`` method of the `ComponetActivity` class wil not be executed, and you aoo may not world properly or crash.

The ``setContent{}`` block is a way to define the UI of your activity using Jetpack Compose, when you calling the MyApp composable function, which presumably contains the UI elements of you app.
NOTE: The ``setContent{}`` block should be called only once in your activity's `onCreate()` method, after calling `super.onCreate()`. If you need to update the UI based on some state changes, you should use state hoisting, modifiers, or effects inside you composable function, rather than calling `setContent{}` again.

The ``Suface()`` composable is a way to create a material surface in Jetpack Compose, a material surface is a container that can have a background color, a border, a shape, and an elevation.

The ``Surface()`` composable takes several parameters, such as:

``modifier``: a Modifier that can be used to apply layout, drawing, or interaction behavior to the surface, such as padding, alignment or click ability.

``shape``: a shape that define the outline of the surface, such as rectangle, a circle, or a custom shape.
``color``: a Color that specifies the background color of the surface.

``contentColor``: a Color that specifies the color of the content inside the surface, such as text or icons.
``border```: a Border that defines the width and color of the border around the surface. If not provided, there is no border.

``elevation``: a Dp that specifies the elevation of the surface, which affects the shadow and the overlay of the surface. If not provided, it defaults to zero.