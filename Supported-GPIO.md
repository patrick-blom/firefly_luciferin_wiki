**Luciferin** supports three different GPIO:
- **GPIO2**
- **GPIO5** (recommended for ESP8266, differently from GPIO2, GPIO5 is not shared with built in LED)
- **GPIO16** 

GPIO can be changed on the fly on both `Full and Light firmware` from the `Firefly Luciferin` settings.

## How to change the GPIO in use?

From the "Devices" tab, double click on the GPIO you want to change, press enter.  
  
<img width="400" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/gpio1.jpg?raw=true">  
  
---
`Firefly Luciferin` will reboot your microcontroller.  
  
<img width="400" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/gpio2.jpg?raw=true">  


## Baud rate

If you are experiencing flickering and your hardware connections is well made, lowering the baud rate may reduce the flicker.

If you want to increase the maximum framerate, highering the baud rate can help.

If you higher the baud rate and your microcontroller doesn't support that speed, you will not be able to change it again until you manually reflash the firmware.

			
