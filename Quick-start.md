## What you don't need  
<img align="right" width="100" height="100" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/java_fast_screen_capture_logo.png">

1) You don't need to be a developer
2) You don't need to be an electrical engineer
3) You don't need a lot of time to complete the job

## What you need  

1) A `Windows PC or Linux` for the screen capture (macOS will be supported soon), captured images are sent to the LED strip that should be positioned behind the monitor.
2) A cheap microcontroler, `ESP8266` is the recommended one.
3) A `WS2812B LED strip`
4) A `power supply` for the LED strip
5) **[OPTIONAL]** An `MQTT Server` or an Home Automation system ex: `Home Assistant`, `OpenHAB`, ecc. 

## Install Glow Worm Luciferin firmware on your microcontroller  

<a href="https://www.wemos.cc/en/latest/d1/d1_mini.html"><img align="right" width="200" src="https://www.wemos.cc/en/latest/_images/d1_mini_v3.1.0_1_16x16.jpg"></a>  

`ESP8266` is the preferred microcontroller and have its own ready to use firmware, it's cheap, it's extremely stable, it have a built in WiFi. If you want to use another microcontroller you can build your own firmware. Wemos and Lolin D1 Mini microcontrollers are premium one. You can't go wrong with them.
- Please install the CH340 driver, download [here](https://www.wemos.cc/en/latest/ch340_driver.html).
- Please download the firmware from [here](https://github.com/sblantipodi/glow_worm_luciferin/releases).
- Flash the firmware on your microcontroller (**FULL version adds support for remote control, if you flash FULL version you MUST** [configure WiFi and MQTT](https://github.com/sblantipodi/firefly_luciferin/wiki/Remote-Access)). **If you flash LIGHT firmware you MUST use USB cable**. You can download ESP Home Flasher from [here](https://github.com/esphome/esphome-flasher/releases).  
This software have an easy GUI and it works great with ESP devices. 

## Connect the LED strip to your microcontroller  

![CIRCUITS](https://github.com/sblantipodi/glow_worm_luciferin/blob/master/assets/img/ambilight_bb.png)
If you have a low quality microcontroller, capacitor, resistance and logic level converter helps "stabilizing the circuit", there are many people who don't use those extra components.
WS2812B led strip is cheap and easy to use and it looks awesome, 5V is easy to manage with a microcontroller, buy a compatible power supply and you are set.  
  
If you don't want to build your own board, you can use a pre-build board like the [QuinLED-Dig-Uno](https://quinled.info/2018/09/15/quinled-dig-uno).  
NOTE: QuinLED-Dig-Uno must be used with Glow Worm FULL Firmware because it can't be connected to your PC via USB.

## Install LED strip behind you monitor
- This is an easy step, a little bit of double sided tape, easy to remove, easy to fix.  
**NOTE:** If you want to use the automatically generated configuration, **your first LED should be positioned in the bottom half of your monitor**. LED strip can be placed clockwise or anticlockwise.

<img width="500" src="https://raw.githubusercontent.com/sblantipodi/firefly_luciferin/master/data/img/moitorled.png">


## Install Firefly Luciferin Java fast screen capture software on your PC  

- Please download and install `Firefly Luciferin` on your PC, you can download it from [here](https://github.com/sblantipodi/firefly_luciferin/releases)
- Once installed the software, start it and configure it via the graphical user interface. Defaults are good for most people.  

![Luciferin](https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/settings_screen.png)

- Connect a USB cable to your ESP8266, double click the tray icon of the `Firefly Luciferin` software and **enjoy your bias lighting system**. If you don't want to connect a USB cable you need to continue reading the Wiki for MQTT/Wireless configuration.

## Want to use it as a lamp, control it remotely, apply special effects to the LED strip, connect it via Home Assistant or OpenHAB?
- [Remote control](https://github.com/sblantipodi/firefly_luciferin/wiki/Remote-Access)
- [Home Automation](https://github.com/sblantipodi/firefly_luciferin/wiki/Home-Automation-configs)