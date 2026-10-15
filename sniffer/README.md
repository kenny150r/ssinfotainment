# CAN Sniffer

ESP32 + single-wire CAN transceiver, running ESP32RET (GVRET protocol) so SavvyCAN can connect to it like a Macchina M2.

## Hardware
- ESP-WROOM-32 dev board
- NCV7356 or TH8056 breakout
- Male OBD-II pigtail

Wiring: see [`../docs/wiring.md`](../docs/wiring.md#sniffer-wiring-esp32--ncv7356).

## Pin assignments

| Function | ESP32 GPIO |
|---|---|
| CAN TX | TBD |
| CAN RX | TBD |

## Firmware
- [ ] Clone ESP32RET, note the commit used here
- [ ] Set board pins for CAN TX/RX
- [ ] Set bus speed to 33.333 kbps (may need a custom bit-timing config)
- [ ] Put the CAN controller in **listen-only** mode for first captures
- [ ] Flash and confirm SavvyCAN connects

Any project-specific firmware changes or config go in `firmware/`.

## Using it
1. Plug into OBD port, USB to laptop.
2. Open SavvyCAN → Connection → add GVRET device (serial or Wi-Fi).
3. Record, then save logs into `../logs/` using the naming convention there.
