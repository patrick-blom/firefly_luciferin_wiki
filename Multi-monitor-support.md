
`Luciferin` supports multi monitor configurations (USB or Wireless through MQTT).  
One microcontroller per monitor is required, this gives you the best possible experience.
- No need for daisy chaining multiple monitors, no flying connection between monitors.
- Easier wiring and easier to troubleshoot.
- No bandwidth problems on the microcontroller for the big amount of LEDs needed.
- Per monitor control, if you have a triple monitor setup, but you want to game on a single monitor, you can do it.

## How to setup multi monitor

- If you are using FULL firmware and you want to use the same MQTT server on all the monitors, please configure MQTT, skip this step if you are using the LIGHT firmware.
<img width="400" src="https://github.com/sblantipodi/firefly_luciferin/blob/dynamic_gpio/data/img/multi_display/multimonitor_1.jpg?raw=true">  
  
- In the "devices" tab, please select dual or triple display as per your preference and click save
<img width="400" src="https://github.com/sblantipodi/firefly_luciferin/blob/dynamic_gpio/data/img/multi_display/multimonitor_3.jpg?raw=true">   
  
- `Luciferin` creates a tray bar icon for each monitor
<img width="100" src="https://github.com/sblantipodi/firefly_luciferin/blob/dynamic_gpio/data/img/multi_display/triple_monitor_tray_grey.jpg?raw=true">  

- Right click the tray icon and configure the number of LEDs you are using on that monitor. 
<img width="400" src="https://github.com/sblantipodi/firefly_luciferin/blob/dynamic_gpio/data/img/multi_display/multimonitor_7.jpg?raw=true">  

- Please configure an output device for each monitor.  
Please use "COM ports" if you are using a USB cable, use "Device Name" if you are using MQTT Stream.
<img width="400" src="https://github.com/sblantipodi/firefly_luciferin/blob/dynamic_gpio/data/img/multi_display/multimonitor_6.jpg?raw=true">  
