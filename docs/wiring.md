# Wiring

Always confirm pinouts with a multimeter before connecting anything.

## OBD-II port (J1962) — pins we use

| Pin | Signal |
|---|---|
| 1 | GM single-wire CAN (body bus) |
| 4 | Chassis ground |
| 5 | Signal ground |
| 6 | High-speed CAN H |
| 14 | High-speed CAN L |
| 16 | Battery +12V (always on) |

The car has the female port; the pigtail is **male** (J1962M).

### Our pigtail's wire colors (fill in after continuity test)

| OBD pin | Wire color |
|---|---|
| 1 | |
| 4 | |
| 5 | |
| 16 | |

## Sniffer wiring (ESP32 + NCV7356, SOIC-8)

NCV7356 pinout: 1 TxD · 2 MODE0 · 3 MODE1 · 4 RxD · 5 VBAT · 6 LOAD · 7 CANH · 8 GND

| From | To | Notes |
|---|---|---|
| OBD pin 1 | NCV7356 pin 7 (CANH) | Optional 47µH series inductor + 100pF to GND for noise |
| OBD pin 16 | NCV7356 pin 5 (VBAT) | 1A inline fuse → 1N4004 diode → pin 5; 10µF + 100nF to GND at the chip |
| OBD pins 4/5 | NCV7356 pin 8 + ESP32 GND | Common ground |
| NCV7356 pin 6 (LOAD) | NCV7356 pin 7 (CANH) | 6.49k load resistor (6.8k fine) |
| NCV7356 pin 1 (TxD) | ESP32 GPIO 25 | CAN TX |
| NCV7356 pin 4 (RxD) | ESP32 GPIO 26 | 2.7k pull-up to **3.3V** |
| NCV7356 pins 2, 3 (MODE0/1) | 3.3V | Both high = normal mode (default is sleep) |
| ESP32 USB | Laptop | Powers the ESP32 while sniffing |

Fill in exact GPIO numbers in `sniffer/README.md` once chosen.

## Stock head unit connector(s) — TBD

Source: (wiring diagram / service manual reference)

| Connector | Pin | Wire color | Signal | Verified? |
|---|---|---|---|---|
| | | | Constant 12V | |
| | | | Accessory / ignition | |
| | | | Ground | |
| | | | SW-CAN | |
| | | | Amp audio outputs | |
| | | | Amp turn-on | |
| | | | Mic + / bias | |
| | | | Mic − | |
| | | | Backup camera video | |
| | | | USB | |

## Measurements

| What | Value | Date |
|---|---|---|
| Mic bias voltage | | |
| Amp input type | | |
| Camera video format | | |
