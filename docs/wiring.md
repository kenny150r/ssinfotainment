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

## Sniffer wiring (ESP32 + NCV7356)

| From | To | Notes |
|---|---|---|
| OBD pin 1 | Transceiver CANH (bus) | Via the breakout's load/filter if present |
| OBD pin 16 | Transceiver VBAT | Add an inline fuse (1A) |
| OBD pins 4/5 | Transceiver GND + ESP32 GND | Common ground |
| Transceiver TxD | ESP32 CAN TX GPIO | Set in firmware |
| Transceiver RxD | ESP32 CAN RX GPIO | Pull-up to **3.3V**, not 5V |
| Transceiver MODE0/MODE1 | Tie for normal mode | Check datasheet |
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
