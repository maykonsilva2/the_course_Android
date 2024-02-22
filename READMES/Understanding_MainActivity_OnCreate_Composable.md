Code structure of the MainActivity.kt file
````kotlin
    class MainActivity : ComponentActivity() {
        override fun onCreate(savedInstanceState: Bundle?) {
            super.onCreate(savedInstanceState)
            setContent {
                MyApp()
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

`super.onCreate(savedInstanceState)`