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

* 3A (Nue) "HGZB-41" - wall switch - Zigbee
* IKEA "LED1924G9" - TRÅDFRI 806 lm RGB - Zigbee
* WLED (ESP & WS2812B) - Wifi

### Mains Voltage "Plugs"

* Tuya "TS011F_plug_1" x3 - plug with voltage, power, ... measurements - Zigbee
* Lidl "HG06337" - plug without measurements - Zigbee
* Peacefair PZEM-004T mains measurement (ESP & PZEM-004T-V3) - Wifi

### Heating & Cooling

* TODO: Xiaomi "Mi Smart Standing Fan 2 EU" - Wifi
* <s>Earu/TuYa "TV02" Radiator Valve</s> fail, just doesn't work - Zigbee

### Audio Output

* MaryTTS - text to speech - Wifi/LAN
* Wifi speaker (ESP32 & Max98357) - Wifi
* <s>Simple buzzer (ESP & TODO Buzzer) - Wifi</s> fail, due to very bad sound quality!
* TODO: Media Player ?
* TODO: Rhasspy ?

### Occupancy

* Sonoff "SNZB-03" x2 - PIR - Zigbee
* TODO: mmWave (ESP & LD2410) - Wifi

### Weather

* OpenWeatherMap - Internet
* Flughafen Nürnberg - Internet
* TODO: Xiaomi Aqara "WSDCGQ11LM" temperature, humidity & air pressure sensor - put in waterproof case on windows sill outside?

### Indoor Climate Sensors

* Xiaomi "LYWSD03MMC" x10 - temperature & humidity sensor with LCD - BLE
* Xiaomi Aqara "WSDCGQ11LM" temperature & humidity & air pressure sensor - Zigbee
* Xiaomi "GZCGQ01LM" x2 - light sensor - Zigbee
* Bosch "BMP280" - air pressure & temperature sensor (ESP & BMP280) - Wifi
* <s>Inkbird IBS-TH1 Plus - BLE</s> fail, due to unreliable data transfer!
* TODO: Adafruit "LTR390" -  UV and ambient light sensor (ESP & LTR390) - Wifi
* TODO: "BH1750" - ambient light sensor (ESP & BH1750) - Wifi
* TODO: Doostman AirCO2ntrol - CO2 sensor (ESP & AirCO2ntrol) - Wifi

### Buttons & Input

* Xiaomi Wireless Switch "WXKG01LM" - single button - Zigbee
* IKEA TRÅDFRI "E1743" - double button - Zigbee
* <s>IKEA STYRBAR "E2001/E2002" - quad button - Zigbee</s> unused
* Tuya Smart Knob "ERS-10TZBVK-AA" - button & rotary encoder - Zigbee
* Aqara Magic Cube "MFKZQ01LM" - various actions - Zigbee

### Door / Window Sensor

* Sonoff "SNZB-04" - door / window sensor - Zigbee

### Display

* LCD 20x4 character display (ESP & 2004 display) - Wifi
* TODO: Android tablet as display? - Wifi

### Computer (over Wifi or LAN)

* HASS.Agent - Windows client
* Home Assistant - Android client
* Ping - sensor
* Web page - sensor (is web page available?)
* Printer - sensor (e.g. toner level)
* SNMP - sensor (e.g. printer page count)
* [Wake-on-LAN](Wake_on_LAN.md) (WoL) - actor
* <s>Speedtest - sensor</s> fail, no response!
* TODO: Windows / Linux - System Monitor

### Unsorted TODO

* TODO: Rhasspy Voice Control
* TODO: Mi Body Composition Scale 2 - body scale
* TODO: NFC
* TODO: Infrared - IR-control in/out
* TODO: OctoPrint ?
* TODO: VideoCam input
* TODO: Calendar / workday based alarm clock
* TODO: Window Cover
* TODO: Aqara "SJCGQ11LM" water sensor - Zigbee

-------------------------------

## TODO: Automations
