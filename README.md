# Home Automation of ulfl

## Server

### Hardware

* [Chuwi "Herobox"](Chuwi_Herobox.md) - Intel Gemini Lake J4125, 8 GB RAM, 256 GB SSD, fanless
* Sonoff "ZBDongle-P" ZigBee USB Stick - with 2m USB expansion cable to avoid interferences

### Software

* Ubuntu Server 20.04 LTS (EOL: Apr. 2025)
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

## Devices, Sensors & DIY Electronics

### ESP32 / ESP8266 microcontroller

* ESP32 & ESP8266 - are used to control various DIY electronics over Wifi
* ESP32 - also used as DIY Wifi to Bluetooth Low Energy (BLE) bridge

### Lighting

* 3A (Nue) "HGZB-41" - wall switch - Zigbee
* IKEA "LED1924G9" - TRÅDFRI 806 lm RGB - Zigbee
* WLED - DIY RGB light (ESP & WS2812B) - Wifi

### Mains Voltage "Plugs"

* Tuya "TS011F_plug_1" x3 - plug with voltage, power, ... measurements - Zigbee
* Lidl "HG06337" - plug without measurements - Zigbee
* Peacefair PZEM-004T - DIY mains measurement (ESP & PZEM-004T-V3) - Wifi

### Heating & Cooling

* TODO: Xiaomi "Mi Smart Standing Fan 2 EU" - Wifi
* <s>Earu/TuYa "TV02" Radiator Valve - Zigbee</s> fail, even the valve alone just doesn't work

### Audio Output

* MaryTTS - text to speech engine - Wifi/LAN
* [MAX98357 Media Player](MAX98357_Media_Player.md) - DIY Wifi speaker (ESP32 & MAX98357) - Wifi
* <s>Rtttl buzzer (ESP & Rtttl Buzzer) - Wifi</s> fail, due to very bad sound quality!
* TODO: Media Player ?
* TODO: Rhasspy ?

### Occupancy

* Sonoff "SNZB-03" x2 - PIR - Zigbee
* TODO: LD2140 - DIY microwave "mmWave" presence detection (ESP & LD2410) - Wifi

### Weather

* OpenWeatherMap - Internet
* Flughafen Nürnberg - Internet
* [TuYa "WSD500A"](TuYa_WSD500A.md) - temperature & humidity sensor (window outside) - ZigBee

### Sensors

* [Xiaomi Mijia "LYWSD03MMC"](Xiaomi_Mijia_LYWSD03MMC.md) x10 - temperature & humidity sensor with LCD - BLE
* Aqara "WSDCGQ11LM" - temperature & humidity & air pressure sensor - Zigbee
  * https://www.aqara.com/eu/temperature_humidity_sensor.html
* [TuYa "WSD500A"](TuYa_WSD500A.md) - temperature & humidity sensor - Zigbee
* Xiaomi "GZCGQ01LM" x2 - light sensor - Zigbee
* Sonoff "SNZB-04" - door / window sensor - Zigbee
* ["BMP280"](BMP280.md) - DIY air pressure & temperature sensor (ESP & BMP280) - Wifi
* <s>[Inkbird IBS-TH1 Plus](Inkbird_IBS-TH1_Plus.md) - temperature & humidity sensor with LCD - BLE</s> - fail, due to unreliable data transfer!
* ["Ikea VINDRIKTNING"](Ikea_VINDRIKTNING.md) - DIY air quality (PM 2.5) sensor (ESP & VINDRIKTNING) - Wifi
* TODO: Adafruit "LTR390" -  DIY UV and ambient light sensor (ESP & LTR390) - Wifi
* TODO: "BH1750" - DIY ambient light sensor (ESP & BH1750) - Wifi
* TODO: TFA Doostmann AirCO2ntrol - DIY CO2 sensor (ESP & AirCO2ntrol) - Wifi

### Buttons & Input

* Xiaomi Wireless Switch "WXKG01LM" - single button - Zigbee
* IKEA TRÅDFRI "E1743" - double button - Zigbee
* <s>IKEA STYRBAR "E2002" - quad button - Zigbee</s> unused
* [Tuya Smart Knob](Tuya_Smart_Knob.md) "ERS-10TZBVK-AA" - button & rotary encoder - Zigbee
* Aqara Cube "MFKZQ01LM" - various actions - Zigbee
  * https://www.aqara.com/eu/cube.html

### Display

* [LCD Character Display](LCD_Character_Display.md) - DIY 20x4 char display (ESP, PCF8574 & display) - Wifi
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
  * https://www.aqara.com/eu/water_leak_sensor.html
* TODO: Bed occupancy sensor (ESP & HX711 based scale) - Wifi

-------------------------------

## TODO: Automations

-------------------------------

## Measurements

### Power Consumption

* [DeLonghi Inissio](power_consumption/delonghi_inissio.md) (Nespresso) coffee maker
