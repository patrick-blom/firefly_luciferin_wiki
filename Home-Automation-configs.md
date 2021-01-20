Thanks to the MQTT protocol **Luciferin** can be easily integrated into your preferred Home Automation systems.

## Home Assistant integration  
<img align="right" width="100" height="100" src="https://avatars3.githubusercontent.com/u/13844975?s=200&v=4">  
  
- Create a `luciferin` folder inside your `conf` folder.
- Copy the [ready to use package](https://github.com/sblantipodi/glow_worm_luciferin/blob/master/home_assistant_luciferin_package.yaml) into your `luciferin` folder.  
  
<img align="center" width="1000" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/ha_luciferin.jpg?raw=true">  


- Add the package to your `configuration.yaml`
```yaml
homeassistant:
  packages:
    luciferin: !include luciferin/luciferin.yaml
```
Once you restarted Home Assistant Core, you can configure a `Vertical Stack` like the one in the image with this:

---  

```yaml
cards:
  - cards:
      - entity: light.glowworm
        type: light
    type: horizontal-stack
  - cards:
      - entities:
          - input_number.pc_animation_speed
        type: entities
    type: horizontal-stack
  - cards:
      - entity: input_boolean.solideffect
        hold_action:
          action: more-info
        icon_height: 50px
        show_icon: true
        show_name: true
        state_color: true
        type: entity-button
      - entities:
          - input_select.gamma_select
        type: entities
    type: horizontal-stack
  - cards:
      - entity:
          - sensor.firefly_luciferin_producing
        max: 30
        min: 0
        type: gauge
        unit: FPS
      - entity:
          - sensor.firefly_luciferin_consuming
        max: 30
        min: 0
        type: gauge
        unit: FPS
      - entity:
          - sensor.gw_fps
        max: 30
        min: 0
        type: gauge
        unit: FPS
    type: horizontal-stack
  - cards:
    type: history-graph
    entities:
      - entity: sensor.firefly_luciferin_producing
      - entity: sensor.firefly_luciferin_consuming
      - entity: sensor.gw_fps
    hours_to_show: 1
    refresh_interval: 5
type: vertical-stack
```

---  

![SCREENSHOT](https://github.com/sblantipodi/glow_worm_luciferin/blob/master/assets/img/HA_mobile_client_screenshot.jpg?raw=true)
  
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