## MQTT support  

**Luciferin** supports `MQTT` and can be controlled via a smartphone or via a PC remotely using a generic MQTT client.

![SCREENSHOT](https://github.com/sblantipodi/pc_ambilight/blob/master/data/img/HA_mobile_client_screenshot.jpg)

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