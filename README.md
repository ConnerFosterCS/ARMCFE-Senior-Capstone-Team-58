# ARMCFE-Senior-Capstone-Team-58

Project: Augmented Reality Maintenance Checks for Equipment
Students: Carle, Joshua  —  Crew, Gabriel  —  Foster, Conner 


### Table of Contents:
Section 1: Purpose \
Section 2: Example Usage \
Section 3: Software Used \
Section 4: Implementation \
Section 5: Problems \
Section 6: How to Run Project \
Section 7: Resources


### Section 1: Purpose
The ARCMFE mobile application makes use of Augmented Reality to simplify maintenance checks on electronic locks by visually displaying the locks information to the user quickly. The scope of this document is to describe the format of this application and the process to recreate it. 


### Section 2: Example Usage
![Program Demo](https://github.com/ConnerFosterCS/ARMCFE-Senior-Capstone-Team-58/blob/main/ExampleUsage.gif)


### Section 3: Software Used
Note: All software that we used is free for developmental purposes (except the Unity BLE scanner package which costs $20), however, a software license is necessary for a distributable product that uses this software.

| Software  | Why it is Used |
| ------------- | ------------- |
| Android OS | The application is built on Android OS because it allows you to upload your own files directly to the phone's file system making development easier. Also, the android applications will work across a large variety of Android OS devices. |
| Unity (Vuforia AR Package) | Unity is the engine containing our 3D project. Vuforia is a package for Unity that we used to be able to “see” the lock with the phone. This is offered for free and is developed by Unity themselves. https://developer.vuforia.com/ |
| Unity (BLE Scanner Package) | Unity is the engine containing our 3D project. Bluetooth LE for iOS, tvOS and Android is a package for Unity that we used to be able to read the BLE lock data within Unity. This is offered for $20 on the unity asset store and is developed by a private publisher. https://assetstore.unity.com/packages/tools/network/bluetooth-le-for-ios-tvos-and-android-26661#content |


### Section 4: Implementation
For the implementation of this project we first created the functioning Vuforia application. This was done by following the instructions provided in this video: https://www.youtube.com/watch?v=y7VD7yGwmV4
This video shows how to use Unity’s Model Target Generator (MTG) which requires a Vuforia account in order to get an access key for the Vuforia plugin. The MTG converts an existing 3D model into a Vuforia Engine database that can be used by the Vuforia Engine for Model Target tracking. We used a 3D model created using the MTG to represent the lock in the virtual environment.

Using built in features of Unity we are able to create a UI that can be attached to and move with the lock once Vuforia is able to establish tracking.  This movement is done by placing all the UI elements into a Canvas object that is set to render by “World Space”. This sets its location to match the tracking data that Vuforia supplies. The UI itself is made from a collection of TextMeshPro and image objects to create the text and visual elements such as the battery and signal bars. Changes to these elements are handled by C# scripts with the battery bar being a small exception, in that it relies on a slider and color gradient components added to its Unity object in addition to a script. These additional components allow for the color changing ability of the battery bar while keeping the script that controls the battery bar as simplified as possible.

The C# scripts themselves are each self contained and control a small portion of the overall UI to allow more modularity. They are simplistic and are used as an intermediate between the UI and the BLE connection. The BLE will hand off information to the scripts and they will alter the UI to reflect the information that the lock is broadcasting. There is minimal processing that the scripts do to this information to keep device requirements as low as possible.

For the BLE connection we used the Bluetooth LE for iOS, tvOS and Android unity plugin. Within this package there are some example scripts/scenes containing base functionality. The scene we were interested in is the ScannerTest. We then modified these scripts to include information about manufacturer data and UUID. The information found with this script is then sent to a .txt to be parsed by the UI visual elements.


### Section 5: Problems
Out of all of the AR methods we attempted, such as an image database and shape recognition, using a 3d model to map points to search for within a 3d space was the most effective method we found. We ran into many problems with the AR features being inconsistent with the other methods.

We originally wanted to develop most of the application in kotlin through android studio since kotlin and android studio have a large amount of support and usage within the android application space, however, we could not figure out how to effectively merge the Unity AR application features into android studio which forced us to read the BLE device information through a Unity package instead.


### Section 6: How to Run Project
APK Instructions 
1. Download the project from github and unzip the file. 
2. Within the file there is an APK titled “ARMCFE App.apk” 
3. Download the APK onto your device and run the application 

Unity Instructions 
1. Download the project from github and unzip the file 
...


### Section 7: Resources
A Youtube tutorial on making a simple Unity AR mobile application via Vuforia: \
https://www.youtube.com/watch?v=MtiUx_szKbI \

Unity BLE scanner package (Bluetooth LE for iOS, tvOS and Android): \
https://assetstore.unity.com/packages/tools/network/bluetooth-le-for-ios-tvos-and-android-26661#publisher \

Unity AR package (Vuforia): \
https://developer.vuforia.com/ 
