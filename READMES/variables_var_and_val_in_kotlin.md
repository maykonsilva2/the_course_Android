## var
Is mutable variable, non-final variable. Once initialized, we're free to mutate the data held by the variable.

````kotlin
    var myMutableVariable: Byte = 1
    myMutableVariable = 2 // mutate the data held by the variable
````
The variable is initializes with the ``int`` data type.

NOTE: we also have the option to specify the data type when we initialize the variable.
````kotlin
    var myMutableVariable: Byte = 1
    var myVariable: Byte = "b" // Error, wrong type.
````

## val
Are read-only, meaning they cannot be reassigned once they are initialized.
You can use ``val`` variable to declare constants or immutable data structures.
for example:  parameters in functions or constructors.

## const
A ``const`` is a variable that is immutable and known at compile-time.
Some  benefits of using ``const`` variables are:
- They are *inlined* by the compiler, meaning they are replaced by their values at the places where they are used. This can improve performance and reduce memory usage.

NOTE: The main difference between ``val`` and ``const`` variables is that ``val``  variables can be initialized at runtime, meaning they can be assigned values from expressions, functions, or classes, while ``const`` variables can only be initialized at compile-time, meaning they can only be assigned values from primitive types or string.