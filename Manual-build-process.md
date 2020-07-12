This guide is meant for developers who wants to customize or build `Fast Screen Capture` from sources.

Fast Screen Capture uses Java 14 Package API to create the Windows installer.

If you are running Windows 8 or Windows 10 you can use Desktop Duplication API (DDUPL), it's the fastest implementation yet, no lag, no stutter, very small usage of resources. DDUPL is accessed via JNA using the GStreamer bindings for Java.
GStreamer is bundled with the installer thanks for the maven-compiler-plugin. 

Wix Toolset binaries is in `/wix311-binaries/` folder.

## Build from source
- Simply git clone the project.
- mvn clean
- mvn install
Maven will create a `FastScreenCapture-x.x.x-jar-with-dependencies.jar` that will be bundled with the installer. The jar is executable.

## Create binary installer for Windows
To create the binary installer, simply run:
- cd wix311-binaries  
- jpackage -i ../target --main-class org.dpsoftware.FastScreenCapture --main-jar JavaFastScreenCapture-jar-with-dependencies.jar --icon ../data/img/java_fast_screen_capture_logo.ico --win-menu --win-menu-group Ambilight --copyright "Davide Perini" --name "Fast Screen Capture"  --vendor DPsoftware --win-dir-chooser --win-shortcut




