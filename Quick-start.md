## What you don't need  
<img align="right" width="100" height="100" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/java_fast_screen_capture_logo.png">

1) You don't need to be a developer
2) You don't need to be an electrical engineer
3) You don't need a lot of time to complete the job

## What you need  

1) A `Windows PC` for the screen capture, captured images are sent to the LED strip that should be positioned behind the monitor.
2) A cheap microcontroler, `ESP8266` is preferred
3) A `WS2812B LED strip`
4) A `power supply` for the LED strip
5) An Home Automation system ex: Home Assistant, OpenHAB, ecc. (optional, not strictly needed)

## Install Glow Worm Luciferin firmware on your microcontroller  

<a href="https://www.wemos.cc/en/latest/d1/d1_mini.html"><img align="right" width="170" src="https://www.wemos.cc/en/latest/_images/d1_mini_v3.1.0_1_16x16.jpg"></a>  

`ESP8266` is the preferred microcontroller and have its own ready to use firmware, if you want to use another microcontroller you can build your own firmware. Wemos and Lolin D1 Mini microcontrollers are premium one. You can't go wrong with them.
- Please install the CH340 driver, download [here](https://www.wemos.cc/en/latest/ch340_driver.html)
- Please download the firmware from [here](https://github.com/sblantipodi/glow_worm_luciferin/releases)
- Flash the firmware on your microcontroller. You can download ESP Home Flasher from [here](https://github.com/esphome/esphome-flasher/releases).  
This software have an easy GUI and it works great with ESP devices.

## Connect the LED strip to your microcontroller  

![CIRCUITS](https://github.com/sblantipodi/pc_ambilight/blob/master/data/img/ambilight_bb.png)
If you have a low quality microcontroller, capacitor, resistance and logic level converter helps "stabilizing the circuit", there are many people who don't use those extra components.
WS2812B led strip is cheap and easy to use and it looks awesome, 5V is easy to manage with a microcontroller, buy a compatible power supply and you are set.

## Install Firefly Luciferin Java fast screen capture software on your PC  

- Please download and install Firefly Luciferin on your PC, you can download it from [here](https://github.com/sblantipodi/firefly_luciferin/releases)
- Once installed the software, start it and configure it via the graphical user interface  

![IMAGE ALT TEXT HERE](https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/settings_screen.png)




-----
**If you want to use WiFi and connect the microcontroller to an MQTT network for remote management or to integrate `Luciferin` with an home automation system like Home Assistant or OpenHAB