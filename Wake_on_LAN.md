# Wake-on-LAN

Wake-on-LAN (WoL): **Send a "Magic packet" from Home Assistant to remotely wakeup a sleeping computer**

*State (2023.02): WoL works just fine. WoL for my "Cooler" PC doesn't work -> that machine is just too old*

https://en.wikipedia.org/wiki/Wake-on-LAN

A lot of "WoL How Tos" can be found on the web ...

## Reducing PC Power Consumption

Bringing a PC into a deep sleep state (aka: standby) and only waking it up when needed, can SIGNIFICANTLY reduce the power consumption. However, measuring the actual power consumption is a good idea - even a PC in "deep sleep" may consume a noticeable amount of power.

Two examples:
* My Esprimo desktop PC takes much less than 1W in standby (20W in idle).
* My older HP DL380p server takes around 20W even in standby (and around 200W in idle)!

As both machines are only used rarely, I want to reduce permanent power consumption both for environental and cost saving reasons. Set the Esprimo to standby with <1W is ok, but even the standby consumption of the HP server of 20W is too high for the long run. I switch it off completely using a Tuya Mains Plug (with < 1W) when not in use. 

The cost for 1W each year in Nürnberg: 1 W * 24 h * 365 days * 0,4 €/kWh => 3,5 €/year

This results in:
* Esprimo: 3,5€ standby, 70 € idle
* HP DL380p: 3,5€ Tuya Plug, 70 € standby, 700 € idle

TODO: Move this to its own page and describe the different ways how to save power better?

## Troubleshooting

Setting up Wake-on-LAN can be a bit tricky, some hints:

* Check ALL BIOS settings (usually in a section named "power" or "energy")
* Check with a native (Windows or Linux) WoL client before trying with HASS or ESPHome if the PC actually wakes up
* WoL will only work on the same Ethernet/Wifi segment. Router or NAT inbetween may cause problems

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

Using Home Assistant for WoL is easy and should be preferred. If that's not possible (e.g. Home Assistant and the target PC are in different routing segments), ESPHome can be used as a "WoL proxy".

https://esphome.io/components/button/wake_on_lan.html

```
button:
  - platform: wake_on_lan
    name: "Start my Server"
    target_mac_address: E9:48:B8:01:02:03
```
