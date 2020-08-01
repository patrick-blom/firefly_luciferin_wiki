Thanks to the MQTT protocol **Luciferin** can be easily integrated into your preferred Home Automation systems.

## Home Assistant integration
<img align="right" width="100" height="100" src="https://avatars3.githubusercontent.com/u/13844975?s=200&v=4">  

- Create a `glow_worm_luciferin` folder inside your `conf` folder.
- Copy the [ready to use package](https://github.com/sblantipodi/glow_worm_luciferin/blob/master/home_assistant_glow_worm_package.yaml) into your `glow_worm_luciferin` folder.

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

input_number:
  pc_animation_speed:
    name: PC Animation Speed
    initial: 40
    min: 1
    max: 150
    step: 1
    
input_boolean:
  effettosolido:
    name: Bias Light

sensor:
  - platform: mqtt
    state_topic: 'lights/glowwormluciferin'
    name: 'Last Seen GlowWorm'
    value_template: '{{ value_json.time }}'    
  - platform: mqtt
    state_topic: 'lights/glowwormluciferin'
    name: 'GlowWorm Version'
    unit_of_measurement: ' '
    value_template: '{{ value_json.ver }}'   
    
automation:
  - id: '1548456985521'
    alias: GlowWorm ON
    trigger:
    - entity_id: input_boolean.effettosolido
      from: 'off'
      platform: state
      to: 'on'
    action:
    - data:
        payload: '{"JFSC": "STOP"}'
        topic: lights/glowwormluciferin/set
      service: mqtt.publish    
    - delay: 00:00:04
    - data:
        payload: '{"state": "ON", "effect": "solid"}'
        topic: lights/glowwormluciferin/set
      service: mqtt.publish
  - id: '1548456985522'
    alias: GlowWorm OFF
    trigger:
    - entity_id: input_boolean.effettosolido
      from: 'on'
      platform: state
      to: 'off'
    action:
    - data:
        payload: '{"JFSC": "START"}'
        topic: lights/glowwormluciferin/set
      service: mqtt.publish    
    - delay: 00:00:04    
    - data:
        payload: '{"state": "ON", "effect": "GlowWorm"}'
        topic: lights/glowwormluciferin/set
      service: mqtt.publish
  - id: '3845456985522'
    alias: GlowWorm OFF JFSC
    trigger:
      platform: mqtt
      topic: lights/glowwormluciferin/set
      payload: '{"state": "ON", "effect": "GlowWorm"}'
    action:
    - service: input_boolean.turn_off
      data:
        entity_id: input_boolean.effettosolido
  - id: '3845456985521'
    alias: GlowWorm ON JFSC
    trigger:
      platform: mqtt
      topic: lights/glowwormluciferin/set
      payload: '{"state": "ON", "effect": "solid"}'
    action:
    - service: input_boolean.turn_on
      data:
        entity_id: input_boolean.effettosolido        
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