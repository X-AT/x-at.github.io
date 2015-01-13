---
layout: post
title:  "X-AT arduino based control board"
date:   2015-01-13 12:56:00
categories: xat
---

At project start i wanted to use TL-WR703N GPIO's for direct control.
But when i pulled out almost all gpio from openwrt table, i found that only few of that really accessible.
So i decide to add simple USB bridge based on sparkfun arduino pro micro (china clone costs less than atmega32u4 on local market).

With this mod it now closer to [SatNOGS][satnogs] project, but i don't like their decision to use CDC and additional serial protocol.
My board almost the same as [SatNOGS-arduino][satnogs-ar], but with different wiring, I2C for Adafruit OLED display and voltage divider for battery monitoring.

![schematic](/images/arduino-board/x-at-arduino.sch.png)
![x-at-arduino control board](/images/arduino-board/IMG171.jpg)

TODO:

- Check QTR-1RC endstops
- Check *V<sub>bat</sub>* voltage meter (A0)
- Simple LUFA HID device
- Add bulk endpoint for LCD
- Port AccelStepper
- SSD1306 support

Done:

- Check stepper drivers
- Check SSD1306 OLED display


[satnogs]: http://satnogs.org
[satnogs-ar]: https://github.com/satnogs/satnogs-arduino
