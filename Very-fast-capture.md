## Why is it fast? What is the achievable framerate?
Firefly Luciferin is written in Java using AWT's Robot class, Robots is the only way to screen capture using Java (without exotic libs).  
With that thing you can almost never get above 5FPS (in 4K) because as you can see in the OpenJDK implementation, `robot.createScreenCapture()` is synchronized and the native calls it uses are pretty slow.  
Fast enough for screenshots but too slow for screen capture. If one Robot can capture at about 5FPS, what about 2 Robots in a `multi threaded producer/consumer` environment?  
What about adding `GPU Hardware Acceleration` to the mix?

## What is the Performance Impact on your System?
Firefly Luciferin is a very optimized software and it has **nearly no impact on your system performance**.  
By default Firefly Luciferin captures at 30FPS, if you want you can unlock the framerate.  
  
If you are using a slow microcontroller, capturing at a very high framerate will not help. If you right click the tray icon and then click `FPS`,
you can see the output as shown in the image below. In that output you can see how fast the software is capturing the screen (producing)
and how fast your microcontroller is able to process (consume) this data.  

<p align="center">
  <img width="700" src="https://raw.githubusercontent.com/sblantipodi/firefly_luciferin/master/data/img/framerate_counter_javafx_menu.png">
</p>

Increase `dataRate` accordingly to your microcontroller's serial speed, 115200 is generally more than enough for 30FPS and 100 LEDs. Producers framerate should not exceed the consuming one, all data that is not consumed in time, is lost.

## GPU Hardware Acceleration using Java Native Access 
Screen capturing is pretty slow and very CPU intensive in Windows systems (Linux is much more efficient in this regard),
for this reason I wrapped the Windows GDI32 C class using [Java Native Access](https://github.com/java-native-access/jna) to access Windows hardware acceleration.  

This API captures and delivers captured frames in GPU memory. 

If you are running Windows 8 or Windows 10 you can use `Desktop Duplication API (DDUPL)`, it's the fastest implementation yet, no lag, 
no stutter, very small usage of resources. DDUPL is accessed via [JNA](https://github.com/java-native-access/jna) using the [GStreamer bindings for Java](https://gstreamer.freedesktop.org/bindings/java.html).  
