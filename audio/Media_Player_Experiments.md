# Media Player Experiments

My speaker experiments (aka: "media player") for Music Assistant.

State (2024.07): My DIY ESP32 & PCM5102A media player connected to the existing audio amplifier works nice. Sonos connection is unstable in Music Assistant.

## Sonos

My recently bought Sonos speakers (Ikea Symfonisk Bookshelf Gen.2) currently (2024.07) have trouble of **"randomly" re- and disappearing** from Music Assistant (bugfix/reimplementation work seems to be currently ongoing).

* [Ikea Symfonisk Bookshelf Gen.2](https://www.ikea.com/de/de/p/symfonisk-regal-wifi-speaker-weiss-smart-generation-2-50506587/) (Ikea Deutschland)
* [https://music-assistant.io/player-support/sonos/](https://music-assistant.io/player-support/sonos/) (Music Assistant: Sonos specific infos)

Initially, the Music Assistant "playbar" wasn't noticing when the speaker is playing something - so I could start a track but couldn't even stop the playing. Reason for this was the firewall (ufw) on the docker container host which "filtered" the notifications from the speaker to Music Assitant.

These speakers are suitable for kitchen/bathroom but not for intense listening IMHO.

## DIY: squeezelite ESP32 & PCM5102A

Next idea was to use squeezelite ESP32 as a "WiFi audio bridge" and connect it via cable to my existing audio amplifier. So I've tried to setup squeezelite with an ESP32 WROVER & PCM5102A, but **got stuck by the overwhelming amount of settings** of the squeezelite ESP32 web page. While the documentation shows many possibilities, it isn't very good and I couldn't find an easy to follow guide.

Hardware: ESP32 WROVER board needed (with 4 MB PSRAM), an ESP32 WROOM (or an ESP8266) will NOT work. I2S stereo DAC (e.g. PCM5102A)

* [https://github.com/sle118/squeezelite-esp32?tab=readme-ov-file](https://github.com/sle118/squeezelite-esp32?tab=readme-ov-file) Project page
* [https://sle118.github.io/squeezelite-esp32-installer/](https://sle118.github.io/squeezelite-esp32-installer/) Web based installer (only supports Chrome or Edge)

I didn't dig very deep and will probably have a second try on it.

## DIY: ESPHome, ESP32 & MAX98357

Then I've tried my old DIY Heco speaker "recently" equipped with ESP32 & MAX98357 (Mono DAC & 3W amplifier) that is working ok in Home Assistant. This way I checked if Music Assistant works with it. The setup in Music Assistant was easy once the connection between MASS and HASS was ok.

* [Home Assistant Media Player in Music Assistant](home_assistant_media_player.md) (how to setup the media player in MASS)
* Build your own [MAX98357 media player](MAX98357_Media_Player.md) (many detailed DIY infos)

**The speaker chassis quality is not suitable for intense listening** but proved that this way works stable with Music Assistant and encouraged me to try the setup with ESP32 & PCM5102A below.

## DIY: ESPHome, ESP32 & PCM5102A

I now created a DIY "WiFi stereo audio bridge" to my existing amplifier with an ESP32 WROOM & PCM5102A (Stereo DAC) using ESPHome. This simply "converts" WiFi to audio without any EQ or other options. I've read many times that you should use squeezelite for DIY with an ESP32 WROVER (but without explanations why). So I wasn't sure if my simpler setup would work at all, produces sound problems or whatever.

* [Home Assistant Media Player in Music Assistant](home_assistant_media_player.md) (how to setup the media player in MASS)
* Build your own [PCM5102A media player](PCM5102A_Media_Player.md) (many detailed DIY infos)

Well, **it works good.**
