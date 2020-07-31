## Why it's fast? What is the achievable framerate?
Firefly Luciferin is written in Java using AWT's Robot class, Robots is the only way to screen capture using Java (without exotic libs).  
With that thing you can almost never get above 5FPS (in 4K) because as you can see in the OpenJDK implementation, `robot.createScreenCapture()` is synchronized and the native calls it uses are pretty slow.  
Fast enough for screenshots but too slow for screen capture. If one Robot can capture at about 5FPS, what about 2 Robots in a `multi threaded producer/consumer` environment?  
What about adding `GPU Hardware Acceleration` to the mix?

## CPU load with 6 threads
With 6 threads and an i7 5930K @ 4.2GHz I can capture at 25FPS in 4K (no GPU), 12 threads gives me +30FPS.   
If you want, you can increase threads numbers variable and get even higher framerate.  

Note: performance does not increase linearly, find the sweet spot for your taste and your environment.  
`Maximum framerate` is generally achieved by setting thread number at a value greater than your CPU cores, if you  
have a 8 cores CPU, best framerate is achieved with 16 threads.  
  
![CPU LOAD](https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/smashing_threads.jpg)

If you are using a slow microcontroller, capturing at a very high framerate does not help. If you right click tray icon and then click `FPS`,
you can see the output as shown in the image below. In that output you can see how fast the software is captruing the screen (producing)
and how fast your microcontroller is able to process (consume) this data.  

<p align="center">
  <img width="700" src="https://raw.githubusercontent.com/sblantipodi/firefly_luciferin/master/data/img/framerate_counter_javafx_menu.png">
</p>

Increase `dataRate` accordingly to your microcontroller's serial speed, 115200 is generally more than enough for 30FPS and 100 LEDs. Producers framerate should not exceed the consuming one, all data that is not consumed in time, is lost.

## GPU Hardware Acceleration using Java Native Access (for Windows only) 
Screen capturing is pretty slow and very CPU intensive in Windows systems (Linux is much more efficient here),
for this reason I wrapped the Windows GDI32 C class using [Java Native Access](https://github.com/java-native-access/jna) to access Windows hardware acceleration.  

This API capture and deliver captured frames in GPU memory. It's fast but not enough for my tastes because it adds 
a little bit of lag to the mouse and is a CPU hog.  

If you are running Windows 8 or Windows 10 you can use `Desktop Duplication API (DDUPL)`, it's the fastest implementation yet, no lag, 
no stutter, very small usage of resources. DDUPL is accessed via [JNA](https://github.com/java-native-access/jna) using the [GStreamer bindings for Java](https://gstreamer.freedesktop.org/bindings/java.html).  

## TODO
- Add Linux/MacOS support, don't use on Linux or MacOS yet. 