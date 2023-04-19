# Home Automation of ulfl

## Server

### Hardware

* Chuwi Herobox - Intel Gemini LakeJ4125, 8 GB RAM, 256 GB SSD
* Sonoff "ZBDongle-P" ZigBee USB Stick - with 2m USB expansion cable to avoid interferences

### Software

* Ubuntu Server 20.04 LTS
* Docker

### Docker Container
* Home Assistant
* Mosquitto - MQTT broker
* Zigbee2MQTT - Zigbee bridge
* InfluxDB - time series DB
* MariaDB - SQL DB
* MaryTTS - Text to Speech engine
* ESPHome - ESP32 & ESP8266 microcontroller "configuration"

... containers updated regularly using Watchtower

TODO: Add links to the container images

------------------------

## Devices & Sensors

### ESP32 / ESP8266 microcontroller

* ESP32 & ESP8266 - are used to control various electronics over Wifi
* ESP32 - also used as Wifi to Bluetooth Low Energy (BLE) bridge

### Lighting

* Wandschalter - Zigbee
* IKEA TRÅDFRI RGB - Zigbee
* WLED (ESP & WS2812B) - Wifi

### Occupancy

* Sonoff PIR - Zigbee
* TODO: mmWave (ESP & LD2410) - Wifi

### Mains Voltage

* Tuya Mains Plug - Zigbee
* PZEM mains measurement (ESP & PZEM-004T-V3) - Wifi

### Climate (Outdoor)

* OpenWeatherMap - Internet
* Flughafen Nürnberg - Internet
* TODO: Mi temp&hum in waterproof case ? - Zigbee

### Climate (Indoor)

* Mi LYWSD03MMC Temperature & Humidity - BLE
* Mi Temp&Hum&Pressure - Zigbee
* <s>Inkbird - BLE</s> fail due to unreliable data transfer!
* TODO: UV and ambient light (ESP & TODO) - Wifi
* TODO: Ambient Light (ESP & BH1750) - Wifi
* TODO: Mi Fan (TODO: own category?) - Wifi
* TODO: CO2 (ESP & CO2 TODO) - Wifi

### Audio Output

* MaryTTS - Wifi/LAN
* Audio amplifier (ESP & Max98357 or other I2S amplifier chips) - Wifi
* <s>Simple buzzer (ESP & TODO Buzzer) - Wifi</s> fail due to very bad sound quality!
* TODO: Media Player ?
* TODO: Rhasspy ?

### Buttons

* Mi Wireless Switch - single button - Zigbee
* IKEA TRÅDFRI - double button - Zigbee
* IKEA STYRBAR - quad button - Zigbee
* Tuya Smart Knob - button & rotary encoder - Zigbee

### Display

* LCD character display (ESP & 2004 display) - Wifi
* TODO: Android tablet as display? - Wifi

### Computer (over Wifi or LAN)

* HASS.Agent - Windows client
* Home Assistant - Android client
* Ping - sensor
* Web page - sensor (web page available)
* Printer - sensor (e.g. toner level)
* SNMP - sensor (e.g. printer page count)
* [Wake-on-LAN](Wake_on_LAN.md) (WoL) - actor
* <s>Speedtest - sensor</s> fail!
* TODO: System Monitor

### Unsorted / TODO

* TODO: Rhasspy Voice Control
* Mi Scale - body scale
* TODO: NFC
* TODO: Infrared - IR-control in/out
* TODO: OctoPrint ?
* TODO: VideoCam input
* TODO: Calendar / workday
* TODO: Window Cover

-------------------------------

## TODO: Automations
