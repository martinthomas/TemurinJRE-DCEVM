# TemurinJRE-DCEVM

This READme is borrowed from https://github.com/james-epting/AdoptOpenJRE-DCEVM as is the idea.  Added the Github Actions to create the output files in a semi-automated manner by implementing the instructions below written by James Epting.

Since the creation of the original READme, some things have changed - the AdoptOpen website is now pointing to Adoptium's Temurin binaries.

## Github Actions

I created a Github Action workflow for both OSX and Win64 which will pull the source files and then follow the instructions from James to create a new JRE package.  The new package will then be added as an artifact to the workflow run and to a pull request to this repo.

The workflows are osx_manual.yaml and win64_manual.yaml

The workflows have default parameters for the source for the JRE, JDK and Trava bundles which are, at time of writing, the latest.  If you need to, you can provide different values.
The current values for Windows are:

- https://github.com/adoptium/temurin11-binaries/releases/download/jdk-11.0.20.1+1/OpenJDK11U-jdk_x64_windows_hotspot_11.0.20.1_1.zip
- https://github.com/adoptium/temurin11-binaries/releases/download/jdk-11.0.20.1+1/OpenJDK11U-jre_x64_windows_hotspot_11.0.20.1_1.zip
- https://github.com/TravaOpenJDK/trava-jdk-11-dcevm/releases/download/dcevm-11.0.15+1/Openjdk11u-dcevm-windows-x64.zip
  
As a side note - Github Actions are cool.

## Original READme 

The original file continues below without any modifications

-------------------------

The files in this project are Java Runtime Environments from [AdoptOpenJDK](https://adoptopenjdk.net/index.html?variant=openjdk11&jvmVariant=hotspot) with the [DCEVM](http://dcevm.github.io/) from [TravaJDK](https://github.com/TravaOpenJDK) added

To use the DCEVM JRE, point to it to be used by your application as a JRE. While your application is running you can make changes to it and then see those changes take effect by recompiling the changed classes.

There is also some example Java code here to illustrate what DCEVM can do, the java example can be run as a Console Application. This sample code mimics an application server, it has a 30 second start up, and 5 minute run time. Here you can make changes and watch the "log activity" reflect those changes. Don't forget to point to the DCEVM JRE, and to recompile your classes!

In order to make this DCEVM JRE I copied the JVM file from [Trava JDK 11 ](https://github.com/TravaOpenJDK/trava-jdk-11-dcevm) into the [AdoptOpenJDK's JRE](https://adoptopenjdk.net/archive.html?variant=openjdk11&jvmVariant=hotspot), I also added the modules file from AdoptOpenJDK into the JRE.

To replicate what I did here are the steps you need to take

## Windows
  1. Download AdoptOpenJDK's JRE
  2. Download AdoptOpenJDK 
  3. Download TravaJDK
  4. Extract all downloaded files
  5. Copy {TravaJDK Directory}/bin/server/jvm.dll to {JRE Directory}/bin/server/jvm.dll
  6. Copy {AdoptOpenJDK Directory}/lib/modules to {JRE Directory}/lib/modules
  
## OSX
  1. Download AdoptOpenJDK's JRE
  2. Download AdoptOpenJDK 
  3. Download TravaJDK
  4. Extract all downloaded files, to open the extracted files you may need to right click and select "Show Package Contents"
  5. Copy {TravaJDK Directory}/Contents/Home/lib/server/libjvm.dylib to {JRE Directory}/Contents/Home/lib/server/libjvm.dylib 
  6. Copy {AdoptOpenJDK Directory}/Contents/Home/lib/modules to {JRE Directory}/Contents/Home/lib/modules

### Licensing Information
This project is licensed under the [Apache License v2](https://www.apache.org/licenses/LICENSE-2.0)

TravaJDK license information can be viewed here: [Click me!](https://github.com/TravaOpenJDK/trava-jdk-11-dcevm/blob/master/LICENSE)

AdoptOpenJDK license information can be viewed here: [No! Click me instead!](https://adoptopenjdk.net/about.html?variant=openjdk11&jvmVariant=hotspot)
