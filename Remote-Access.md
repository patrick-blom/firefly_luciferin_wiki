## MQTT support  

**Luciferin** supports `MQTT` and can be controlled via a smartphone or via a PC remotely using a generic MQTT client.

![SCREENSHOT](https://github.com/sblantipodi/glow_worm_luciferin/blob/master/assets/img/HA_mobile_client_screenshot.jpg)

## Default topic
```
lights/glowwormluciferin/set
```

## Turn ON/OFF the LED strip remotely, apply light effects  

```yaml
{"state": "ON"}
```
```yaml
{"state": "OFF"}
```
```yaml
{"state": "ON", "effect": "rainbow"}
```

Those are the supported effects:
- GlowWorm
- GlowWormWifi
- bpm
- candy cane
- confetti
- cyclon rainbow
- dots
- fire
- glitter
- juggle
- lightning
- noise
- police all
- police one
- rainbow
- solid rainbow
- rainbow with glitter
- ripple
- sinelon
- solid
- twinkle


## Connect to the WiFi and MQTT network.
Thanks to [Arduino Bootstrapper](https://github.com/sblantipodi/arduino_bootstrapper), **Glow Worm Luciferin** firmware starts an access point for easy configuration via a mobile phone.  
Please connect to the AP with your mobile, if you search for WiFi networks you will find your ESP device named LUCIFERIN, once connected go to http://192.168.4.1 and you will access a GUI where you can enter all the passwords without the needs of hardcoding them.
 
<p align="left">
  <img width="450" src="https://raw.githubusercontent.com/sblantipodi/glow_worm_luciferin/master/assets/img/luciferin_access_point.jpg">
</p>

1) **IP Address:** The IP address that your ESP should use.
2) **SSID:** Your Wifi SSID, the name of your Wifi.
3) **Wifi Password:** Your Wifi password
4) **OTA Password:** You can use this password to update Luciferin via wireless. (same password must be configured in Firefly Luciferin PC software)
5) **MQTT Server IP:** The IP address of your MQTT server.
6) **MQTT Server Port:** The port of your MQTT server. 
7) **MQTT Username:** The username you use to login to your MQTT server.
8) **MQTT Password:** Your MQTT password.  
  
**Please double check your input before clicking the 'Store config' button. If you enter wrong data you need to erase the ESP memory and reflash the firmware.**