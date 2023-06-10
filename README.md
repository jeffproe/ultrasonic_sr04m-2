# ultrasonic_sr04m-2
Custom ESPHome Component for the SR04M-2 waterproof ultrasonic sensor

Based off of the ultrasonic component in [ESPHome](https://github.com/esphome/esphome)

Example YAML:

```
esphome:
  name: sonartest
  friendly_name: SonarTest

external_components:
  - source:
      type: local
      path: my_components

esp32:
  board: esp32dev
  framework:
    type: arduino

# Enable logging
logger:

# Enable Home Assistant API
api:
  encryption:
    key: !secret esphomeapipwd

ota:
  password: !secret esphomeotapwd

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password

  # Enable fallback hotspot (captive portal) in case wifi connection fails
  ap:
    ssid: "Sonartest Fallback Hotspot"
    password: !secret ap_password

captive_portal:

sensor:
  - platform: ultrasonic_sr04m-2
    trigger_pin: 
      number: 14
      inverted: true
    echo_pin: 13
    name: "Ultrasonic Sensor"
    timeout: 3.0m
    pulse_time: 20us
```