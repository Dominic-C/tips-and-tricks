# Installing Android Studio on Ubuntu

## Pre-requisites
### Java JDK and JRE
At the time of writing, i used a PPA to download java onto my ubuntu systems.
```
    sudo add-apt-repository ppa:linuxuprising/java 
    sudo apt-get update 
    sudo apt-get install oracle-java10-installer
```
then we can run 
```
    sudo apt-get install oracle-java10-set-default
```
to set java10 as our default java version.

 
## Downloading Android Studio
* Download the zip folder for android studio from the official [webpage](https://developer.android.com/studio/)
* Unpack the `.zip` folder in to /opt
* to launch android studio, go to `android-studio/bin` and execute `studio.sh`

### Adding Android Studio to PATH
To add android studio to your PATH, add this line to the end of your `.bashrc`.
```
    export PATH="$PATH:/opt/android-studio/bin"
```
Note: putting $PATH: before your file location gives it a lower priority than system files. This is the recommended way to add path to your system because PATHs defined by Linux developers will have higher priority on execution.

in other words, we are appending the PATH to our priority list instead of prepending it.

## Installing Drivers for physical Android Device
run `sudo apt-get install android-tools-adb`. Then follow the instructions written in this [github repository](https://github.com/snowdream/51-android) to install the necessary udev rules into your system.

## Using git with android studio projects
When uploading android projects to github, include the gradle files if you want the programs to be able to run right after pulling. If you did'nt know, Android studio has a built in git control system.

## Developing for Android with Java
There are two main languages we can use to write Java apps. One of them is Kotlin, and the other is Java.

Here is a link to a playlist for developing Android Apps with Java, recommended by my professor: [Getting Started with Android Development](https://www.youtube.com/watch?v=viRDj9jFjSk&list=PLXiaMWHbNgp0I0FnFiUh7o4TDACd9ETs6)