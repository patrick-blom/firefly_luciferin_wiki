[**Glow Worm Luciferin**](https://github.com/sblantipodi/glow_worm_luciferin) is a firmware designed for **ESP8266/ESP32 microcontrollers**.  
**ESP8266 is the recommended microcontroller for Luciferin**, it's cheap, it's fast, it's small, it has enough memory and built in WiFi, its ecosystem is generally more mature than other microcontrollers.  
If you want to use another microcontroller you can build your own firmware.  
Wemos and Lolin D1 Mini microcontrollers are premium ones.  

## Lolin D1 Mini ESP8266
|  ESP                 |  Board                         |
|----------------------|--------------------------------|
|<a href="https://www.wemos.cc/en/latest/d1/d1_mini.html"><img width="400" src="https://github.com/wemos/docs/raw/master/docs/en/_static/boards/d1_mini_v3.1.0_1_16x16.jpg"></a>|<a href="https://www.wemos.cc/en/latest/d1/d1_mini.html"><img width="400" src="https://github.com/wemos/docs/raw/master/docs/en/_static/boards/d1_mini_v3.1.0_2_16x16.jpg"></a>|

A mini wifi board with 4MB flash based on ESP-8266EX.
[Buy it](https://www.aliexpress.com/store/product/D1-mini-Mini-NodeMcu-4M-bytes-Lua-WIFI-Internet-of-Things-development-board-based-ESP8266/1331105_32529101036.html)  

## ESP32
|  ESP                 |  Board                         |
|----------------------|--------------------------------|
|<a href="https://docs.wemos.cc/en/latest/d32/d32.html"><img width="400" src="https://docs.wemos.cc/en/latest/_images/d32_v1.0.0_1_16x16.jpg"></a>|<a href="https://docs.wemos.cc/en/latest/d32/d32.html"><img width="400" src="https://docs.wemos.cc/en/latest/_images/d32_v1.0.0_2_16x16.jpg"></a>|  

A wifi&bluetooth board based ESP-32 [Buy it](https://www.aliexpress.com/store/product/WEMOS-LOLIN32-V1-0-0-wifi-bluetooth-board-based-ESP-32-4MB-FLASH/1331105_32808551116.html) 

Thanks to [Arduino Boostrapper](https://github.com/sblantipodi/arduino_bootstrapper) it can run on a lot of devices but if you want to run of a different board than ESP8266/ESP32, you need to manually compile the firmware.

## LED Strip WS2812B 5V
60 LEDs per meter is generally bright enough for most applications and does not require a lot of power.

<img width="500" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/ledstirp.jpg?raw=true">

[WS2812B 5V LED strip](https://it.aliexpress.com/wholesale?catId=0&initiative_id=SB_20200731160829&origin=y&SearchText=WS2812B+5v)

## Power supply for the LED strip
You need to buy a [power supply](https://it.aliexpress.com/wholesale?catId=0&initiative_id=SB_20200731160904&SearchText=5v+power+supply) capable of powering all the LEDs you want. For 60 LEDs a power supply of at least 5V/3A it's recommended, for 120 LEDs you need a 5V/6A power supply, do your math here.
A bigger power supply generally works better and runs less hot than a smaller one. **Don't undersize the power supply**.

## Pre-build boards support
If you don't want to build your own board, you can use a pre-build board like the [QuinLED-Dig-Uno](https://quinled.info/2018/09/15/quinled-dig-uno).  
NOTE: QuinLED-Dig-Uno must be used with Glow Worm FULL Firmware because it can't be connected to your PC via USB.
  
<img width="500" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/quinled.png?raw=true">

