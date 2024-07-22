# I2S and ESP32

I2S "Inter-IC Sound" https://en.wikipedia.org/wiki/I%C2%B2S is used to connect the ESP32 microcontroller with audio chips. I2S is available on the ESP32 only (incl. ESP32 WROOM, ESP32 WROVER, ESP32 S2, ESP32 S3 and ESP32 C3), **an ESP8266 won't work**.

## I2S Audio Output

The ESPHome "I2S Audio Media Player" https://esphome.io/components/media_player/i2s_audio.html can use different I2S chips (e.g. UDA1334A, PCM5102A or MAX98357).

These chips contain a mono or stereo DAC https://en.wikipedia.org/wiki/Digital-to-analog_converter and some other components in a single chip. Some contain a mono audio power amplifier.

## I2S Audio Input

The ESPHome "I2S Audio Microphone" https://esphome.io/components/microphone/i2s_audio.html can be used with "all in one" I2S microphone chips (e.g. INMP441).

I couldn't find an ADC "analog audio in" breakout board, that could be used to digitize analog sources like vinyl or tape recordings.

## I2S ESPHome Base

For both output and input you also need to configure the "I2S Audio Component" https://esphome.io/components/i2s_audio

## I2S Chip Overview

Likely incomplete overview (2024.07) of easy to purchase "breakout boards" with I2S chips:

| Chip | Function | Price for PCB | Remarks | Link | Picture |
| --- | --- | --- | --- | --- | --- |
| PCM5102A | Stereo DAC | ~2 € | 112 bB SNR | [PCM5102A Media Player](PCM5102A_Media_Player.md) | ![PCM5102A](images/PCM5102A_PCB_top.jpg) |
| PCM5122A | Stereo DAC | ~15 € | PCM5102A with I2C config? PCB designed as "Pi hat" | https://esphome.io/components/media_player/i2s_audio.html |
| UDA1334A | Stereo DAC | ~4 € | Chip seems discontinued | https://esphome.io/components/media_player/i2s_audio.html |
| MAX98357 | Mono DAC & 3W power amplifier | ~2 € | 3W (4 Ω), 1.4W (8 Ω) | [MAX98357 Media Player](MAX98357_Media_Player.md) | ![MAX98357 board](images/MAX98357_board.jpg) |
| NS4168 | Mono DAC & 2.5W power amplifier | ~14 € | Only as M5Stack module, no standalone PCB | https://esphome.io/components/media_player/i2s_audio.html |
|INMP441 | Mono microphone | ~2 € | | https://esphome.io/components/microphone/i2s_audio.html | ![INMP441](images/INMP441.jpg) |

The ESP32 internal DAC (8 bit) seems a bit noisy: https://community.home-assistant.io/t/esphome-i2s-media-player-internal-dac/434280 so this was not an option for me.

## Bus Lines

For output chips you'll use:

| Line | Function | ESPHome yaml |
| --- | --- | --- |
| BCLK / SCK | bit clock | i2s_bclk_pin |
| LRCLK / WS | left right clock / word select | i2s_lrclk_pin |
| DOUT / SD | serial data (output) | i2s_dout_pin |

For audio input chips you'll use:

| Line | Function | ESPHome yaml |
| --- | --- | --- |
| BCLK / SCK | bit clock | i2s_bclk_pin |
| LRCLK / WS | left right clock / word select | i2s_lrclk_pin |
| DIN / SD | serial data (input) | i2s_din_pin |

TODO: I haven't tried I2S for input or connecting both input and output to a single ESP32, however this should be possible.

TODO: Add physical infos: Max. frequency, voltages, ...