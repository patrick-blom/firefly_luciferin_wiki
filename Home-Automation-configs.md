Thanks to the MQTT protocol **Luciferin** can be easily integrated into your preferred Home Automation systems.

## Home Assistant integration  
<img align="right" width="100" height="100" src="https://avatars3.githubusercontent.com/u/13844975?s=200&v=4">  

- Create a `luciferin` folder inside your `conf` folder.
- Copy the [ready to use package](https://github.com/sblantipodi/glow_worm_luciferin/blob/master/home_assistant_luciferin_package.yaml) into your `luciferin` folder.  

<img align="center" width="1000" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/ha_luciferin.jpg">  
---  
```yaml
light:
  - platform: mqtt
    schema: json
    name: "GlowWorm"
    state_topic: "lights/glowwormluciferin"
    command_topic: "lights/glowwormluciferin/set"
    effect: true
    effect_list:
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
    brightness: true
    rgb: true
    optimistic: true
    #transition: 1000

input_select:
  gamma_select:
    name: "Gamma"
    options:
      - 1.0
      - 1.8
      - 2.0
      - 2.2
      - 2.4
      - 4.0
      - 5.0
      - 6.0
      - 8.0
      - 10.0
    initial: 2.2
    icon: mdi:gamma

input_number:
  pc_animation_speed:
    name: PC Animation Speed
    initial: 40
    min: 1
    max: 150
    step: 1

input_boolean:
  solideffect:
    name: Luci effetto solido

sensor:
  - platform: mqtt
    state_topic: 'lights/firelyluciferin/framerate'
    name: 'Luciferin Producing'
    unit_of_measurement: 'FPS'
    value_template: '{{ value_json.producing }}'
  - platform: mqtt
    state_topic: 'lights/firelyluciferin/framerate'
    name: 'Luciferin Consuming'
    unit_of_measurement: 'FPS'
    value_template: '{{ value_json.consuming }}'    
  - platform: mqtt
    state_topic: 'lights/glowwormluciferin'
    name: 'GlowWorm Version'
    unit_of_measurement: ' '
    value_template: '{{ value_json.ver }}'
  - platform: mqtt
    state_topic: 'lights/glowwormluciferin'
    name: 'Glow Worm Luciferin'
    unit_of_measurement: 'FPS'
    value_template: '{{ value_json.framerate }}'  

automation:
  - id: '1548456985521'
    alias: GlowWorm Solid Effect ON
    trigger:
      - entity_id: input_boolean.solideffect
        from: 'off'
        platform: state
        to: 'on'
    action:
      - data:
          payload: '{"JFSC": "STOP"}'
          topic: lights/glowwormluciferin/set
        service: mqtt.publish
  - id: '1548456985522'
    alias: GlowWorm Solid Effect OFF
    trigger:
      - entity_id: input_boolean.solideffect
        from: 'on'
        platform: state
        to: 'off'
    action:
      - data:
          payload: '{"JFSC": "START"}'
          topic: lights/glowwormluciferin/set
        service: mqtt.publish
  - id: '3845456985522'
    alias: GlowWorm Solid Effect OFF JFSC
    trigger:
      platform: mqtt
      topic: lights/glowwormluciferin/set
      payload: '{"state": "ON", "effect": "GlowWorm"}'
    action:
      - service: input_boolean.turn_off
        data:
          entity_id: input_boolean.solideffect
  - id: '1345456985522'
    alias: GlowWorm Solid Effect OFF JFSC Wifi
    trigger:
      platform: mqtt
      topic: lights/glowwormluciferin/set
      payload: '{"state": "ON", "effect": "GlowWormWifi"}'
    action:
      - service: input_boolean.turn_off
        data:
          entity_id: input_boolean.solideffect
  - id: '3845456985521'
    alias: LGlowWorm Solid Effect ON JFSC
    trigger:
      platform: mqtt
      topic: lights/glowwormluciferin/set
      payload: '{"state": "ON", "effect": "solid"}'
    action:
      - service: input_boolean.turn_on
        data:
          entity_id: input_boolean.solideffect
  - id: '4321674486'
    alias: PC Animation Speed
    initial_state: true
    trigger:
      - platform: state
        entity_id: input_number.pc_animation_speed
    action:
      - service: mqtt.publish
        data_template:
          topic: lights/glowwormluciferin/set
          payload: '{"transition":{{ trigger.to_state.state | int }}}'
  - alias: Set Luciferin Gamma
    trigger:
    - entity_id: input_select.gamma_select
      platform: state
    action:
    - service: mqtt.publish
      data_template:
        topic: "lights/firelyluciferin/gamma"
        retain: "false"
        payload: '{"gamma":"{{states.input_select.gamma_select.state}}"}'
  - alias: Set HA Gamma
    trigger:
      platform: mqtt
      topic: "lights/firelyluciferin/gamma"
    action:
      service: input_select.select_option
      data:
        entity_id: input_select.gamma_select
        option: "{{ trigger.payload_json.gamma }}"

switch:
  - platform: mqtt
    name: "rebootglowworm"
    command_topic: "cmnd/glowwormluciferin/reboot"
    state_topic: "stat/glowwormluciferin/reboot"
    qos: 1
    retain: false
    payload_on: "ON"
    payload_off: "OFF"
```

- Add the package to your `configuration.yaml`
```yaml
homeassistant:
  packages:
    luciferin: !include luciferin/luciferin.yaml
```
  
![SCREENSHOT](https://github.com/sblantipodi/glow_worm_luciferin/blob/master/assets/img/HA_mobile_client_screenshot.jpg)
  
## Google Home integration via HA
Please configure [Google Home with Home Assistant](https://www.home-assistant.io/integrations/google_assistant),
then add this lines to your `configuration.yaml` file

```yaml
google_assistant:
  ...
  expose_by_default: false
  entity_config:
    light.glowworm:
      name: "glowworm"
      room: 'Roomname'
```  
  
Be sure that your `ESP8266` is connected to WiFi/MQTT network, [quick guide here](https://github.com/sblantipodi/firefly_luciferin/wiki/Remote-Access).