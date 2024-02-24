Reference:
- [Packages and imports](https://kotlinlang.org/docs/packages.html): In this Documentation we will learn about the packages and imports in Kotlin.

Summaries:
A ``package``  is a way of organizing Kotlin files in a project
Each Kotlin file can belong to single package.

````kotlin
package org.example

    fun printMessage() {
        /*...*/
    }

    class Message {
        /*...*/
    }

````
- The full name of the function `printMessage` is `org.example.printMessage`, and the full name of the class `Message` is `org.example.Message`.

A ``import`` is a way of accessing the entities declared in a different package from the current file.

````kotlin
    import org.example.Message // Message is now accessible without qualification.
    import org.test.* // everything is 'org.test' becomes accessible.
````

If there is a name conflict, you can use ``as`` to rename locally the imported entity.
````kotlin
    import org.example.Message // Message is accessible
    import org.test.Message as TestMessage // TestMessage represents 'org.test.Message'
````
``import`` is not restricted to importing classes; you can also use it to import other declarations:
top-level functions and properties;
function and properties declared in objects;
enumeration constants, etc.