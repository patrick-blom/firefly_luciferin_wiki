This guide is meant for developers who wants to customize or build **Firefly Luciferin** from sources.

**Firefly Luciferin** uses `Java 14` Package API to create the Windows/Linux installer.

If you are running Windows 8 or Windows 10 you can use Desktop Duplication API (DDUPL), it's the fastest implementation yet, no lag, no stutter, very small usage of resources. DDUPL is accessed via JNA using the GStreamer bindings for Java.
`GStreamer` is bundled with the installer thanks for the maven-compiler-plugin. 

If you want to use your custom GStreamer SDK you need:
- GStreamer core
- GStreamer system plugins
- GStreamer system plugins for capturing

Wix Toolset binaries is in `/wix311-binaries/` folder.

## Build from source
- Simply git clone the project.
- mvn clean
- mvn install  

Maven will create a `FireflyLuciferin-jar-with-dependencies.jar` that will be bundled with the installer. Generated jar is executable.

## Create binary installer for Windows/Linux
To create the binary installer, simply run:
#### For Windows
- cd wix311-binaries  
- jpackage -i ../target --main-class org.dpsoftware.JavaFXStarter --main-jar FireflyLuciferin-jar-with-dependencies.jar --icon ../data/img/java_fast_screen_capture_logo.ico --win-menu --win-menu-group Ambilight --copyright "Davide Perini" --name "Firefly Luciferin"  --vendor DPsoftware --win-dir-chooser --win-shortcut --win-per-user-install

#### For Linux
jpackage -i target --main-class org.dpsoftware.JavaFXStarter --main-jar FireflyLuciferin-jar-with-dependencies.jar --icon data/img/java_fast_screen_capture_logo.png --linux-shortcut --copyright "Davide Perini" --name FireflyLuciferin  --vendor DPsoftware --app-version "${{steps.get-id.outputs.id}}"

**Firefly Luciferin** has a (continuos integration pipeline)[https://github.com/sblantipodi/firefly_luciferin/actions] that creates the Windows Linux installer on every Git Tag.
