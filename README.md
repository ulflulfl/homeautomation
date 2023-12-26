# Home Automation of ulfl

Home automation related infos. Collected for myself, but may help others ...

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

## "Ready Made" Devices & DIY Electronics

Most devices should be very safe to use as they run with batteries, low voltages (e.g. USB) or normal mains voltage plugs.

**Warning: A few devices below require installation to 110/230V mains voltage with bare wires. Making mistakes can kill you here. Work with mains voltage wires only, if you really know what you are doing!**

### ESP32 / ESP8266 microcontroller

* ESP32 & ESP8266 - are used to control various DIY electronics over Wifi
* ESP32 - used as DIY Wifi to Bluetooth Low Energy (BLE) bridge (for [Xiaomi Mijia "LYWSD03MMC"](Xiaomi_Mijia_LYWSD03MMC.md))
* ESP32 - used as DIY Wifi to Bluetooth proxy (for [Oral-B "Genius X"](Oral-B_Genius_X.md) and LED strip controller)

### Lamping

* IKEA "LED2003G10" - light bulb 1055 lm warm & cold white - Zigbee
* IKEA "LED2103G5" x3 - light bulb 806 lm warm white - Zigbee
* Lonsonho "ZB-RGBCW" - LED strip controller 12V RGBCCT - Zigbee
* LED strip controller "no name" x3 - USB LED controller with very limited range! - Bluetooth
* 3A (Nue) "HGZB-41" - wall switch (beware: mains voltage wires!) - Zigbee
* Girier/Tuya "JR-ZDS01" - mini smart switch (beware: mains voltage wires!) - Zigbee
* <s>IKEA "LED1924G9" - TRÅDFRI 806 lm RGB - Zigbee</s> unused
* <s>WLED - DIY RGB light (ESP & WS2812B) - Wifi</s> unused

### Mains Voltage

* Tuya "TS011F_plug_1" x3 - mains plug with measurements of voltage, power, ... - Zigbee
* Lidl "HG06337" - mains plug without measurements - Zigbee
* Tuya "PJ-1203A" - power monitor 2 channel for DIN rail (beware: mains voltage wires!) - Zigbee
* <s>Peacefair PZEM-004T - DIY mains measurement (ESP & PZEM-004T-V3) (beware: mains voltage wires!) - Wifi</s> -> no longer used due to low resolution of measurements, "PJ-1203A" is much better

### Heating & Cooling

* Earu "TV02-Zigbee" - radiator valve - Zigbee
* TODO: Xiaomi "Mi Smart Standing Fan 2 EU" - Wifi
* <s>Earu/TuYa "TV02" - radiator valve - Zigbee</s> fail, even the valve alone just doesn't work

### Audio Output

* TODO: Media Player ?
* TODO: Rhasspy ?
* <s>MaryTTS - text to speech engine - Wifi/LAN</s> - TTS on Android tablet used instead
* <s>Rtttl buzzer (ESP & Rtttl Buzzer) - Wifi</s> - TTS on Android tablet used instead
* <s>[MAX98357 Media Player](MAX98357_Media_Player.md) - DIY Wifi speaker (ESP32 & MAX98357) - Wifi</s> - unused

### Occupancy

* Sonoff "SNZB-03" x8 - PIR (passive infrared) sensor - Zigbee
* Tuya "ZY-M100-S_2" x2 - human presence sensor (5.8 GHz) - Zigbee
* Sonoff "SNZB-06P" - human presence sensor (5.8 GHz) - Zigbee
* Bed occupancy sensor - DIY with ESP32, see: https://medium.com/@qz_li/smart-bed-7de9ad55276e - Wifi
* <s>LD2140 - DIY microwave "mmWave" presence detection (ESP & LD2410) - Wifi</s> - unused, "ready made 5.8 GHz sensors" used instead

### Weather

* OpenWeatherMap - Internet
* [TuYa "WSD500A"](TuYa_WSD500A.md) - temperature & humidity sensor (located at my window outside) - ZigBee
* <s>Flughafen Nürnberg - Internet</s> - fail, due to unreliable data transfer!

### Indoor Air

* [Xiaomi Mijia "LYWSD03MMC"](Xiaomi_Mijia_LYWSD03MMC.md) x11 - temperature & humidity sensor with LCD - BLE
* Aqara "WSDCGQ11LM" x2 - temperature & humidity & air pressure sensor - Zigbee
  * https://www.aqara.com/eu/temperature_humidity_sensor.html
* [Ikea "VINDRIKTNING"](Ikea_VINDRIKTNING.md) - DIY air quality (PM 2.5) sensor (ESP & VINDRIKTNING) - Wifi
* [Sensirion "SHT31"](Sensirion_SHT31.md) - DIY temperature & humidity sensor - (ESP & SHT31) - Wifi
* [Sensirion "SCD41"](Sensirion_SCD41.md) - DIY CO2, temperature & humidity sensor (ESP & SCD41) - Wifi
* [Sensirion "SGP30"](Sensirion_SGP30.md) - DIY TVOC and eCO2 sensor (ESP & SGP30) - Wifi
* [Sensirion "SPS30"](Sensirion_SPS30.md) - DIY PM1, PM2.5, PM4 and PM10 sensor (ESP & SPS30) - Wifi
* TODO: TFA Doostmann "AirCO2ntrol mini" - DIY CO2 sensor (ESP & AirCO2ntrol) - Wifi
* <s>["BMP280"](BMP280.md) - DIY air pressure & temperature sensor (ESP & BMP280) - Wifi</s> - unused
* <s>[Inkbird IBS-TH1 Plus](Inkbird_IBS-TH1_Plus.md) - temperature & humidity sensor with LCD - BLE</s> - fail, due to unreliable data transfer!

### Other Sensors

* Xiaomi "GZCGQ01LM" x2 - light sensor - Zigbee
* Sonoff "SNZB-04" x3 - door / window contact - Zigbee
* [Oral-B "Genius X"](Oral-B_Genius_X.md) - toothbrush with sensors - Bluetooth
* TODO: Aqara "SJCGQ11LM" water sensor - Zigbee
  * https://www.aqara.com/eu/water_leak_sensor.html
* TODO: Adafruit "LTR390" -  DIY UV and ambient light sensor (ESP & LTR390) - Wifi
* TODO: "BH1750" - DIY ambient light sensor (ESP & BH1750) - Wifi

### Buttons & Input

* Xiaomi Wireless Switch "WXKG01LM" - single button - Zigbee
* Tuya "TS0044" x2 - 4 gang scene switch - Zigbee
* IKEA TRÅDFRI "E1743" - double button - Zigbee
* <s>IKEA STYRBAR "E2002" - quad button - Zigbee</s> - unused, its a bit bulky
* <s>[Tuya Smart Knob](Tuya_Smart_Knob.md) "ERS-10TZBVK-AA" - button & rotary encoder - Zigbee</s> unused (eats batteries?)
* <s>Aqara Cube "MFKZQ01LM" - various actions - Zigbee</s> - unused, usage confuses me :-)
  * <s>https://www.aqara.com/eu/cube.html</s>

### Display & Control

* Pritom "L8+" - 8" Android tablet as display & controller - Wifi
* Samsung "Galaxy Tab A8" - 10.1" Android tablet as display & controller - Wifi
* <s>[LCD Character Display](LCD_Character_Display.md) - DIY 20x4 char display (ESP, PCF8574 & display) - Wifi</s> unused, maybe used again later with 3D printed case

### Computer (over Wifi or LAN)

* HASS.Agent - Windows client with limited system monitor
* Home Assistant - Android client with limited system monitor
* System Monitor - values limited, as Home Assistant is running in a docker container
  * https://www.home-assistant.io/integrations/systemmonitor/
* Ping - sensor (tests if devices are available over LAN or Wifi)
  * https://www.home-assistant.io/integrations/ping/
* Web page - sensor (tests if web page is available)
* Printer - sensor (e.g. printer toner level)
* SNMP - sensor (e.g. printed page count)
  * https://www.home-assistant.io/integrations/snmp/
* [Wake-on-LAN](Wake_on_LAN.md) (WoL) - actor
* <s>Speedtest - sensor</s> fail, no response!

### Unsorted TODO

* TODO: Rhasspy Voice Control
* TODO: Mi Body Composition Scale 2 - body scale
* TODO: NFC tags
* TODO: Infrared - IR-control in/out
* TODO: 3D printer / OctoPrint ?
* TODO: VideoCam input
* TODO: Calendar / workday based alarm clock
* TODO: Window blinds ?
* TODO: Bed occupancy sensor (ESP & HX711 based scale) - Wifi

-------------------------------

## TODO: Automations

-------------------------------

## Measurements

### Power Consumption

* [DeLonghi Inissio](power_consumption/delonghi_inissio.md) (Nespresso) coffee maker
