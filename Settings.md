As soon as you start the `Firefly Luciferin` software it creates a `FireflyLuciferin.yaml` file in your documents folder, you can configure it manually or via user interface.
`If you don't know how to configure it, just use the default settings`.  
If you are using the FULL firmware you must configure [Wifi and MQTT](https://github.com/sblantipodi/firefly_luciferin/wiki/Remote-Access), if you are using the LIGHT firmware you must disable MQTT.

![settings_screen](https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/settings_screen.png?raw=true)

```yaml
---
numberOfCPUThreads: 3     // more threads more performance but more CPU usage
captureMethod: "DDUPL"    // WinAPI and DDUPL enables GPU Hardware Acceleration, CPU uses CPU brute force only
serialPort: "AUTO"        // use "AUTO" to autodetect Serial Port, "COM7" for COM7 
dataRate: 500000          // faster data rate helps when using more LEDs or higher framerate
timeout: 2000             // timeout in serial port detection
screenResX: 3840          // screen resolution width
screenResY: 2160          // screen resolution height
osScaling: 150            // OS scaling feature
gamma: 2.2                // gamma correction for the LED strip
mqttServer: "OPTIONAL"    // MQTT Server protocol://host:port (E.g. "tcp://192.168.1.3:1883")
mqttTopic: "OPTIONAL"     // MQTT Server Topic used to start/stop screen capture on the microcontroller
mqttUsername: "OPTIONAL"  // MQTT Server username
mqttPwd: "OPTIONAL"       // MQTT Server pwd
ledMatrix:                // Auto generated LED Matrix
  Letterbox:
    1:
      x: 2596
      y: 1590
    2:
      x: 2694
      y: 1590
  ...
```

## Gamma correction for HDR contents
Small gamma correction values results in brighter LEDs but less accurate colors.  
2.2 is generally good for `SDR contents`, a value between 4.0 and 6.0 is generally good for `HDR contents`.

## Dynamically generated test image
GUI offers a dynamically generated test image to test the LEDs behind your monitor.  

![](https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/testimage_luciferini.jpg?raw=true)

## Choose "static" colors without external programs

![](https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/misc_tab.jpg?raw=true)
  
![](https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/misc_tab_color.jpg?raw=true)

