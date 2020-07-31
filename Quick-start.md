## What you don't need
1) You don't need to be a developer
2) You don't need to be an electrical engineer
3) You don't need a lot of time to complete the job

## What you need
1) A `Windows PC` for the screen capture, captured images are sent to the LED strip that should be positioned behind the monitor.
2) A cheap microcontroler, `ESP8266 or ESP32` is preferred
3) A `WS2812B LED strip`
4) A `power supply` for the LED strip
5) An Home Automation system ex: Home Assistant, OpenHAB, ecc. (optional, not strictly needed)

## Install Glow Worm Luciferin firmware on your microcontroller
`ESP8266 or ESP32` are the preferred microcontrollers and have their own ready to use firmware, if you want to use another microcontroller you can build your own firmware.

- Please download the firmware from [here](https://github.com/sblantipodi/glow_worm_luciferin/releases)
- Flash the firmware on your microcontroller. You can download ESP Home Flasher from [here](https://github.com/esphome/esphome-flasher/releases).  
This software have an easy GUI and it works great with ESP devices.

## Install Firefly Luciferin Java fast screen capture software on your PC
- Please download and install Firefly Luciferin, you can download it from [here](https://github.com/sblantipodi/firefly_luciferin/releases)




-----
**If you want to use WiFi and connect the microcontroller to an MQTT network for remote management or to integrate `Luciferin` with an home automation system like Home Assistant or OpenHAB