# Wake-on-LAN

Wake-on-LAN (WoL) is used to wakeup a sleeping computer by sending a special Ethernet/Wifi "magic packet". Let the computer "deep sleep" can reduce power consumption a lot.

https://en.wikipedia.org/wiki/Wake-on-LAN

*State (2023.02): WoL works just fine. WoL for "Cooler" PC doesn't work -> that machine is just too old*

Setting up Wake-on-LAN can be a bit tricky, some hints:

* Check ALL BIOS settings (usually in a section named like "power" or "energy")
* Check with a native (Windows or Linux) WoL client before trying with HASS or ESPHome if the PC actually wakes up
* WoL will only work on the same Ethernet/Wifi segment. Router or NAT inbetween may cause problems

A lot of "WoL How Tos" can be found on the web ...

## Reducing PC Power Consumption

Bringing a PC into a deep sleep state and only waking it up when needed, can SIGNIFICANTLY reduce the power consumption. However, measuring the actual power consumption is a good idea - even a PC in "deep sleep" may consume a noticeable amount of power.

Two examples:
* My Esprimo desktop PC takes much less than 1W in standby (20W in idle).
* My older HP DL380p server takes around 20W even when sleeping (and around 200W in idle)! I switch it completely off using a Tuya Mains Plug when not in use. 

## Home Assistant

https://www.home-assistant.io/integrations/wake_on_lan/

*config/configuration.yaml*:

```
wake_on_lan:

switch:
  - platform: wake_on_lan
    name: server_wol
    mac: d8:9d:67:01:02:03
```

## ESPHome
https://esphome.io/components/button/wake_on_lan.html

```
button:
  - platform: wake_on_lan
    name: "Start my Server"
    target_mac_address: E9:48:B8:01:02:03
```
