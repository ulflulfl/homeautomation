# Sensirion SCD41

**Sensor of CO2**, Temperature and Humidity with I2C interface

*State (2023.12): The SCD41 is a "real" CO2 sensor which is working well. Calibration can be a bit tricky (as with other CO2 sensors)*

![SCD41 board with connection wires (the orange wire is not connected)](images/SCD41.jpg)
*SCD41 board with connection wires (the orange wire is not connected)*

Technical data:

* Model: Sensirion SCD41
* Functions: CO2, temperature and humidity sensor
* Measured CO2 range: 400~5000 ppm (accuracy: +-(50ppm +2.5-5% of reading), resolution: 1 ppm)
* Measured temperature range: -10~60°C (accuracy: +-0.8°C, resolution: 0.01°C)
* Measured humidity range: 0~100% RH (accuracy: +-6% RH, resolution: 0.01% RH)
* Dimensions (PCB): 23x13x8 mm
* Interface: I2C
* I2C address: 0x62
* Supply voltage: 2.4~5.5 V
* Maximum current: 205 mA (peak), 18 mA (average)

For detailed infos about the SCD41 accuracy, see the datasheet:
https://sensirion.com/media/documents/48C4B7FB/6426E14D/CD_DS_SCD40_SCD41_Datasheet_D1_052023.pdf

More infos:
* https://emariete.com/en/sensor-co2-sensirion-scd40-scd41/

Aliexpress: 20 € (2023.12)

--------

## Hardware

### CO2 Sensor Selection

The SCD41 is a "Photoacoustic NDIR sensor" which actually measures the CO2 concentration.

Hint: Some cheap "fake" CO2 sensors (like the ams CCS811) try to "calculate" the CO2 value from other measured values, which doesn't really work. The so called eCO2 value from a Sensirion SGP30 is practically unusable for me.

Comparing the available "real" CO2 sensors (Sensirion SCDxx, Amphenol/Teluire T6xxx, Winsen MH-Z19x, SenseAir S8, ...), the SCD41 seems to be the best sensor considering the price/performance. However, the price/performance ratio is close between these sensors - you get what you pay for.

### Bill of Material

Beside the SCD41 on a breakout board, I'm using an ESP 8266 based "D1 mini" board. Other ESP 8266 or ESP 32 boards should work as well.

* SCD41 on breakout board
* ESP 8266 "D1 mini" or alike
* some jumper wires
* power supply: e.g. USB micro cable and power adapter

### Connections

Connections from the "D1 mini" to the SCD41:

| D1 mini | SCD41 |
| --- | --- |
| GND | GND |
| 3V3 | VCC |
| D1 | SCL |
| D2 | SDA |

### Power Supply & Consumption

The SCD41 takes up to 205 mA (peak) and can be powered by the 3.3V from the D1 mini (or similiar) boards. Using 5V would also be possible.

### Calibration

The wonderful world of CO2 sensor calibration ...

While the changes of measured values over short time periods are usually quite accurate, even brand new sensors can have a constant offset to the "real" CO2 value. So they need to be calibrated.

There are several ways to calibrate such a sensor. In a professional environment, the sensor is exposed to a gas source with a known CO2 concentration and calibrated accordingly. Such reference gas cylinders with a CO2 concentration of e.g. 1000 ppm are above 200€ (https://en.safetygas.com/co2-calibration-gas-cylinder-carbon-dioxide), so not really suitable for a DIY approach.

A similiar approach is to use outside fresh air that usually has a CO2 concentration of slightly more than 400 ppm (I've read somewhere that 2022 was usually 419 ppm). A "forced calibration" can be manually triggered when in fresh air. An "automatic calibration" will look a time period (e.g. one week) for the lowest measured value and expects this to be fresh air with ~400 ppm. Both approaches will go wrong (measured values too low) if the sensor is not exposed to fresh air during calibration.

More sophisticated (and expensive) sensors like the Amphenol/Telaire T6615 have a dedicated reference gas chamber that is used for calibration without any external dependencies.

There are different names, sequences and boundary conditions for such a calibration procedure, it's best to consult the sensors datasheet for further details.

--------

## ESPHome

https://esphome.io/components/sensor/scd4x.html

```
...

# I2C
# https://esphome.io/components/i2c
# a D1 mini is used here
i2c:
  sda: GPIO4 # D2
  scl: GPIO5 # D1

# SCD41
# https://esphome.io/components/sensor/scd4x.html
  - platform: scd4x
    temperature_offset: 4.5
    altitude_compensation: 309m
    co2:
      name: "SCD41 CO2"
    temperature:
      name: "SCD41 Temperature"
    humidity:
      name: "SCD41 Humidity"
```

The *temperature_offset* of 4.5°C was determined by comparing it to other measured temperature values. The default is 4°C, so that's already pretty close.

The "altitude_compensation" of 309m is the elevation of Nürnberg. You could also use a barometric sensor (e.g. BMP280) instead. More details can be found at the ESPHome page of the sensor.

If I understand it correct, both adjustments won't affect the CO2 measurement.

## Home Assistant

```
TODO: code snippet 
```

TODO: Screenshot 

-------------------------

## Conclusion

The SCD41 is a "proper" CO2 sensor that returns reasonable results. Comparing the measured values with my "TFA Dostmann AirCo2ntrol Mini", I see a constant difference of ~300 ppm, which I expect to be a calibration issue. Time will tell if a proper "fresh air calibration" will correct these differences.

Measuring CO2 is the main purpose of this sensor. The accuracy of the temperature and humidity measurements isn't groundbreaking.

-------------------------

## Images

![Back of the SCD41 board without any components](images/SCD41_back.jpg)
*Back of the SCD41 board without any components*
