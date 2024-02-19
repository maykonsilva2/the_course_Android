Reference: 
- [Gradle for Developers](https://www.geeksforgeeks.org/gradle-for-android-developers/): In this article, we will deep dive into the Gradle build System and we will learn:

1. What exactly is Gradle?
2. What is Gradle’s role in Android development?
3. Gradle for Android is a Gradle plugin for Android.
4. What exactly are Gradle Plugins?
5. Why is there more than one build.gradle file in an Android project?
6. What do the various fields in the project-level build.gradle file mean?
7. What exactly is a Gradle task? How do I make my own Gradle Task?
8. How can we use the command line to build Gradle?

Summaries and tips:

**Using the command line to run Gradle tasks**
 
``.gradlew assembleDebug --console plain`` - Execute this command, the gradle will build the project and generate the APK file  in the build/outputs/apk/debug directory.
``./gradlew tasks`` - This command will display all the tasks that are available for the project.

**Creating unique tasks**
-Assume we want to clean up the project by creating a custom task. This task can be added to the project's ``build.gradle`` file. The task will delete the build directory and all its contents. The task can be created as follows:

```gradle
    task cleanBuild(type: Delete) {
        delete rootProject.buildDir
    }
   
   //cleanBuild is the name of the task that we have created.
```
- The same result can be obtained by selecting "Clean Project" from the "Build" menu.

One example of how to use a custom tasks:
    - Assume that after we build our APK using the `assembleDebug` process, we want to copy the APK to the Desktop and rename it to something other. 
    We going to do it:
```Gradle
    task getDebugAppInDesktopFolder(dependsOn: 'assembleDebug') {
    doLast {
        def destination = "Put the desired path here"
        def desiredName = "Put the desired name here"
        ext.apk = file("build/outputs/apk/debug/actual-name-of-your-APK-file.apk")

        if(ext.apk.exists()){
            copy {
                    from ext.apk.absolutePath
                    into destination
                    rename {desiredName}
                }
            }
    }   
}
```
Explaining the code:
- `task getDebugAppInDesktopFolder(dependsOn: 'assembleDebug')` - This line creates a task called `getDebugAppInDesktopFolder` that depends on the `assembleDebug` task. This means that the `assembleDebug` task will be executed before the `getDebugAppInDesktopFolder` task.

- `doLast` - This is a closure that contains the code that will be executed when the task is run.
- `def destination = "Put the desired path here"` - This line creates a variable called `destination` and assigns it the value of the path where the APK will be copied to, exemplo: `def destination = "/Users/username/Desktop"`.
- `def desiredName = "Put the desired name here"` - This line creates a variable called `desiredName` and assigns it the value of the name that the APK will be renamed to, exemplo: `def desiredName = "my-App.apk"`.
- `ext.apk = file("build/outputs/apk/debug/actual-name-of-your-APK-file.apk")` - This line creates a variable called `ext.apk` and assigns it the value of the path to the APK that was built.
- `if(ext.apk.exists())` - This line checks if the APK exists.
- `copy { from ext.apk.absolutePath into destination rename {desiredName} }` - This line copies the APK to the `destination` and renames it to `desiredName`.