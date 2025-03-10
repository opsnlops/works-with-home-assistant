# works-with-home-assistant

[![Build Status](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Factions-badge.atrox.dev%2Funixorn%2Fworks-with-home-assistant%2Fbadge%3Fref%3Dmain&style=flat)](https://actions-badge.atrox.dev/unixorn/works-with-home-assistant/goto?ref=main)
[![GitHub stars](https://img.shields.io/github/stars/unixorn/works-with-home-assistant.svg)](https://github.com/unixorn/works-with-home-assistant/stargazers)
[![GitHub last commit (branch)](https://img.shields.io/github/last-commit/unixorn/works-with-home-assistant/main.svg)](https://github.com/unixorn/works-with-home-assistant)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [Introduction](#introduction)
  - [Things to think about before choosing between WiFi, Zigbee and Z-Wave](#things-to-think-about-before-choosing-between-wifi-zigbee-and-z-wave)
  - [A note on dimmers](#a-note-on-dimmers)
  - [Please list stuff that _doesn't_ work, too](#please-list-stuff-that-_doesnt_-work-too)
- [Hubs](#hubs)
- [Wifi devices](#wifi-devices)
- [Zigbee](#zigbee)
- [Z-Wave](#z-wave)
- [Ethernet devices](#ethernet-devices)
- [Non-working / Poorly-working devices](#non-working--poorly-working-devices)
- [Other tools](#other-tools)
- [Useful links](#useful-links)
  - [Hardware Vendors with Open Firmwares](#hardware-vendors-with-open-firmwares)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

This is a list of devices that work with [Home Assistant](https://www.home-assistant.io/) with minimal aggravation.

- If you have to reflash a device to use it with HA, please add that to the **Notes** column.
- If you need to add a plugin to Home Assistant before it can be used, add that to **Notes** too.
- If it requires the devices connect to an internet server, even just for initial configuration, **please add that to the Notes for the device**. I want it easy to see which devices won't brick if the vendor goes out of business and also aren't vulnerable to some jackass hacking the company's servers.
- If the device can be reflashed to make it independent of internet servers, please add that to that entry's notes column, preferably with a link to the instructions.

### Things to think about before choosing between WiFi, Zigbee and Z-Wave

Read [Zigbee and WIFI Cooexistence](https://www.metageek.com/training/resources/zigbee-wifi-coexistence.html) on Metageek for more details, but Zigbee can interfere with 2.4GHz WIFI, Z-Wave doesn't. And since a lot of WIFI IOT gear seems to only work on 2.4GHz, you may want to go Z-Wave if you're just starting to buy equipment.

### A note on dimmers

Lutron holds a patent for sending status back to hubs on their RadioRA2 system. Not all Z-Wave or Zigbee dimmers license this patent, so some act weird. Leviton is known to license this patent, and their dimmers work well.

### Please list stuff that _doesn't_ work, too

I encourage you to add entries for things that don't work. Try to be very clear in the notes field what part didn't work so people can be warned off and not waste money on devices which won't work with HA or that don't support HA for all their features.

## Hubs

| Name   | Description                                      | Notes           |
| ------ | ------------------------------------------------ | --------------- |
| [GoControl CECOMINOD016164 HUSBZB-1 USB Hub](https://smile.amazon.com/gp/product/B01GJ826F8) | USB device with both Z-Wave and Zigbee radios. ||

## Wifi devices

If items here need reflashing to work with Home Assistant, please state that in the **Notes** column.

| Name   | Description                                      | Notes           |
| ------ | ------------------------------------------------ | --------------- |
| [OpenGarage.io garage door opener/sensor](https://opengarage.io) | Combination garage door opener and sensor | This is very nice piece of hardware. <li><ul>Completely configurable through its web interface</ul><ul>Usable with a [Blynk](https://blynk.io) template for remote control</ul><ul>IFTTT support</ul><ul>Has a dedicated cross-platform app</ul><ul>A well documented [REST api](https://github.com/OpenGarage/OpenGarage-Firmware/tree/master/docs)</ul><ul>Can send and receive MQTT messages for ingestion by Home Assistant</ul><ul>The firmware source code is on Github, if you want to audit or modify it.</ul><ul>Also has a configurable audible alarm that can sound before opening or closing the garage door</ul></li> |
| [Sonoff S31](https://smile.amazon.com/gp/product/B07YDC6D4D) 15A Smart Plug | WIFI smart plug that includes energy monitoring. You can fit two of these in a standard US outlet. | The native firmware requires you to use an app to configure it (after creating a cloud account) and was a huge pain in the ass on IOS - I never managed to get my iPhone to detect the plug. Fortunately it can easily be reflashed with Tasmota or ESPHome, which work with HA and don't require a cloud account or phone app to set up. |

## Zigbee

| Name   | Description                                      | Notes           |
| ------ | ------------------------------------------------ | --------------- |
| [GE 45856GE Zigbee Smart Switch In-Wall Lighting Control](https://smile.amazon.com/gp/product/B019HTH2A0/) | In-wall switch. | Requires a neutral wire. ||
| [Samsung SmartThings Motion Sensor](https://smile.amazon.com/gp/product/B01IE35PCC) | Detects temperature and motion. ||
| [Samsung SmartThings Water Sensor](https://smile.amazon.com/gp/product/B07F951JDP) | A cheap small water sensor. Reports wet/dry status for the zone. ||
| [Securifi Peanut Smart Plug](https://smile.amazon.com/gp/product/B00TC9NC82) | A small cheap smart plug with controllable power switch. | Reliable cheap smart plug. Claims to also monitor the energy consumption of the plugged-in device, but monitoring doesn't work. These are just big enough that you can't put two of them on the same double outlet. |

## Z-Wave

| Name   | Description                                      | Notes           |
| ------ | ------------------------------------------------ | --------------- |
| [Aeotec Range Extender 6, Z-Wave Plus repeater](https://smile.amazon.com/gp/product/B01M6CKJXC) | Range extender for Z-Wave. | While it works, it's probably more useful to just buy a Z-Wave smart plug than to get a dedicated range extender. |
| [Aeotec Door/Window Sensor 6](https://smile.amazon.com/gp/product/B01E0OMQR6/) | Lower profile door/window open/close sensor. | Aeon Labs ZW112 sold by Aeotec. No longer available, but the smaller depth works really nicely for a clean look, if you can find it. Works well, with a multi-color LED on the back, which you can see flash in the dark when the door opens/closes. Supports some configuration. Battery is built-in and charges via USB. Test magnet location before installing. Home Assistant requires that the reporting type is changed from `Basic Set` to `Binary Report` in the device configuration. |
| [Aeotec Smart Outlet](https://smile.amazon.com/gp/product/B07PJNL5DB/) | 15 Amp. Monitors electricity usage as well as controlling a device. ||
| [Dome Leak Sensor](https://smile.amazon.com/gp/product/B01LXR0B8Q/) | Water leak sensor. |  Reports via Z-Wave when water is detected and also has an audible alarm. <p>I like that it comes with a four foot sensor probe so you can use it in a sump or other awkward location. |
| [Ecolink Door & Window Sensor](https://smile.amazon.com/dp/B01N5HB4U5/) | Window and Door Sensor. | Uses a magnet to sense if the door or window is open or closed. Pairs with Home Assistant very easily, no trickery needed. Comes with white and brown covers in the box. |
| [FIBARO Smart Implant FGBS-222](https://www.amazon.com/dp/B07NDRCTJK/) | Plugin Universal DIY Tool | Allows for connecting: 6 DS18B20 sensors or 1 DHT sensor and  2 2-wire analog sensors, 2 3-wire analog sensor, 2 binary sensors **NOTE: The internal Temp Sensor is too close to other components to be accurately used without compensating. Also requires not included power supply. |
| [First Alert Z-Wave Smoke Detector & Carbon Monoxide Alarm (2nd Generation)](https://smile.amazon.com/gp/product/B08FFB233Y/) | Smoke and Carbon Monoxide Alarm | There's two versions of this, look for the second generation. It has Z-Wave+. The older version is Z-Wave only. Installs in Home Assistant out of the box. Responds very fast to alerts. Runs on two AA batteries. |
| [GE Enbrighten Plug in Z-Wave Smart Switch](https://smile.amazon.com/gp/product/B004AMB3CI/) | Plug-in Single Outlet with button. ||
| [GE Enbrighten Z-Wave Plus Smart Motion Light Switch](https://smile.amazon.com/gp/product/B07226MG2T/) | Decora light switch with built-in motion sensor. | Made by Jasco (model 26931). Works very well as a motion sensing light switch. Motion and light switch are reported, but it's built-in light sensing is not. Configurable through the switch or Z-Wave to stay on when turned on, turn off automatically when motion isn't detected, or to turn on when motion is detected and turn off with a timer. This one seems more configurable than other motion switches. Motion is detected at least 25' away. |
| [GE Enbrighten Z-Wave Plus Smart Motion Sensor](https://smile.amazon.com/dp/B01KQDIU52) | Motion Sensor, battery or USB powered. | Made by Jasco (model 34193). Portable motion sensor whichcan be mounted by screw or tape as well. Can be battery powered (will wait 4 minutes after motion detected to report again), or USB powered (will report immediately without waiting). It's buggy as a battery powered device (thinks it sees motion when it doesn't, and doesn't stop reporting motion sometimes), but works perfectly as a USB powered device. |
| [GE Enbrighten Z-Wave Plus Smart Plug w/2 USB Ports & 2 Outlets](https://smile.amazon.com/gp/product/B0736311QF/) | Plug-in 2 Outlets covering 1 plug. | Made by Jasco. Only covers one plug, and provides two separately controleld plugs along with USB ports. The whole device can be controlled, or each individual power plug can be controlled, and it also has a button for local control. |
| [GE Enbrighten Z-Wave Plus Smart Plug](https://smile.amazon.com/gp/product/B06W9NWFM3) | Outdoor rated, also works as a range extender. ||
| [GE/Jasco Decora Smart Switch](https://smile.amazon.com/gp/product/B01M1AHC3R/) | Wall Switch. 3 Way compatible. | Requires an add-on remote switch to work with 3 way. Supports up to four add-on switches. |
| [GE/Jasco Standard Smart Switch](https://smile.amazon.com/gp/product/B07X6JW72G/) | Wall Switch. 3 Way compatible. | Requires an add-on remote switch to work with 3 way. Supports up to four add-on switches. |
| [Honeywell T6 Pro Series Thermostat](https://smile.amazon.com/gp/product/B07HFL7R44/) | Mid-range thermostat that works with or without Z-Wave. | Without Z-Wave, you're given full control of the schedule. Lots of options are available through the touch screen as well. When it's connected to a Z-Wave network you can configure it to still allow some scheduling on the thermostat, or to allow full control via Z-Wave. Provides temperature and humidity, and allows a large amount of configuration through Z-Wave as well. |
| [Invoelli Black Series Dimmer](https://inovelli.com/black-series-dimmer-switch-z-wave/) | Wall Switch. 3 Way compatible. Dimmer. | Mostly like the Red Series, but not as feature rich. Does not require a neutral wire, but using one is strongly recommended. Setup can be a bit tricky on older open-zwave installs. Read Inovelli's documentation closely before adding it to your system since you will most likely need to update the open-zwave device config first. Once its working, this is an amazing switch! |
| [Inovelli Red Series Fan + Light Switch](https://inovelli.com/red-series-fan-light-switch-z-wave/) | Wall Switch. Allows control of a light and a fan from one switch. | This device is in two parts. One goes in the wall as a normal switch, and one goes into the fan itself. The wall unit talks to the in-fan unit over RF. The fan has low, medium, and high settings. It also has a programming "Breezy" setting where it randomly jumps between fan speeds to simulate wind. Read the install directions closely before adding it to Home Assistant. You might need to update your open-wave device config with the latest version of the XML files, which Inovelli supplies themselves. |
| [Inovelli Red Series Dimmer](https://smile.amazon.com/gp/product/B07S1BMMGH) | Wall Switch. 3 Way compatible. Dimmer| No Neutral required, but recommended. Depending on your Z-wave integration, may need special setup (https://support.inovelli.com/portal/en/kb/inovelli/switches) Energy Monitoring, Scene Control, RGB Notifications|
| [Inovelli Red Series On/Off Switch](https://inovelli.com/red-series-on-off-switch-z-wave/) | Wall Switch. 3 Way compatible. | Requires a neutral. Monitors energy usage, and has a cool LED you can use for notifications. The local relay can be disabled (power is always supplied to the device), making this a great switch to use with smart bulbs. (The buttons can be used a scene controllers in this configuration.) |
| [Leviton DD00R-DLZ 120VAC 60 Hz Decora Digital/Decora Smart Matching Dimmer Remote](https://smile.amazon.com/gp/product/B01AFU1KOY) | Remote in-wall switch for the [DZ6HD-1BZ Dimmer](https://smile.amazon.com/gp/product/B01N4F487U). ||
| [Leviton DZ6HD-1BZ Dimmer](https://smile.amazon.com/gp/product/B01N4F487U) | Dimmer - 600 Watt incandescent or 300W LED or CFL. Requires a neutral wire. | Periodically (roughly every three to six months) I've run into issues where it locks up with the lights stuck on, but if you trigger the airgap functionality (pull the dimmer lever gently till it clicks and the light on the switch goes out, wait five seconds and push it back into place) it reboots and starts working again. |
| [ZOOZ Z-Wave Plus 4-in-1 Sensor ZSE40 V2.0](https://smile.amazon.com/gp/product/B01AKSO80O/) | Motion, light, temperature, and humidity sensor. | Quirky little device. It measures light on a scale of 0-100%, and not lux. Motion reports without timeout since last report. It requires a [templated `binary_sensor`](https://www.home-assistant.io/docs/z-wave/entities/#burglar-entity) to make the burglar sensor work as a motion sensor in Home Assistant. Opsnlops has an [example configuration](https://github.com/opsnlops/ha-config/blob/main/binary_sensors.yaml). |
| [Zooz Z-Wave Plus S2 MultiRelay ZEN16](https://smile.amazon.com/gp/product/B0846DZJD8/) | Dry Contact Relay | Three dry contact relays in one unit. Useful for controlling things like gas fireplaces, or motors. One relay supports 20A, the other two support up to 15A. Installs into HA very easily, and looks like three independent devices. Can be programmed to do things like turn off a relay after X number of minutes / hours as a safety. |

## Ethernet devices

| Name   | Description                                      | Notes           |
| ------ | ------------------------------------------------ | --------------- |
| [ControlByWeb automation devices](https://www.controlbyweb.com) | Full line of ethernet connected components for data acquisition + relay control | These are industrial-quality complete pieces of hardware, no assembly required. <li><ul>Completely configurable through its web interface</ul><ul>Can interface with HA via the MODBUS integration (TCP/IP flavor)</ul><ul>Has a dedicated mobile app for IOS and Android</ul><ul>Fully documented MODBUS protocol for each device<ul><ul>Can operate standalone (independently of HA) monitoring/controlling any process, alert of specific conditions via email, and save logs to FTP</ul></li> |


## Non-working / Poorly-working devices

This section is for things that you've tried and did not get to work with HA, or do work but just not well.

| Name   | Description                                      | Notes           |
| ------ | ------------------------------------------------ | --------------- |
| [Aqara Vibration Sensor](https://smile.amazon.com/gp/product/B07PJT939B) | Mini glass break detector | This was a pita to add to my HA.<p> Once your HA is scanning for new devices, press and hold the button on the sensor for ~5 seconds until the lights flash, then you have to press it again (but don't hold it, press and release) every second or two until HA finds it.<p>Even when I did manage to add it, it kept falling off of the Zigbee mesh, even though other devices within 10 feet of it maintain stable connections. At least it was cheap. |
| [Aqara Water Leak Sensor](https://smile.amazon.com/gp/product/B07D39MSZS) | Water leak detector | Minuses - <p>The manual was unclear on how to put it in pairing mode - press the water droplet icon firmly until the hidden light flashes three times, then let go.<p>After two months of usage I don't recommend it - it drops out of my Zigbee mesh a lot, even though it's five feet from a Smartthings motion detector that has no problems.<p>Pluses - <p>These ship ready to go - no messing with the battery, just press the button and you can add it to your Zigbee mesh. |
| [Amysen RGBW Bulbs](https://smile.amazon.com/gp/product/B07S2487N8/) | Fairly cheap RGBW LED bulbs | These wifi smart bulbs work with Home Assistant with very little issue, however of the 10 or so I purchased over the span of about 3 months, only 3 remain in service. All the failed ones developed a driver whine (screech, really) within a short handful of months time. |

## Other tools

If you're using the Inovelli switches, you can experiment with LDE effects using Nathan Fiscus' [notification calculator](https://nathanfiscus.github.io/inovelli-notification-calc/)

## Useful links

### Hardware Vendors with Open Firmwares

Devices from these vendors work without you having to take them apart and reflash them, and because they're open source, you don't have to worry about them turning off a cloud server somewhere and bricking your devices.

- [Athom Tech](https://www.athom.tech/tasmota) - Sells devices preflashed with [Tasmota](https://tasmota.github.io/docs/) or [ESPHome](https://esphome.io/).
- [CloudFree.shop](https://cloudfree.shop/) - Sell a bunch of stuff that's pre-flashed with [Tasmota](https://tasmota.github.io/docs/).