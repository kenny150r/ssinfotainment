# CAN Bus Notes

## Networks (GMLAN)

| Bus | Speed | OBD pins | What's on it | Our use |
|---|---|---|---|---|
| Single-wire CAN (SW-CAN) | 33.3 kbps | 1 (+ ground 4/5) | Body control module, HVAC, instrument cluster, radio, steering wheel controls | **Main target.** Read and (later) transmit |
| High-speed CAN (HS-CAN) | 500 kbps | 6 (H), 14 (L) | Engine, transmission, ABS | Read only: speed, RPM, gauges |
| LIN | ~19.2 kbps | — | Local switch links | Probably not needed |

To verify on the SS: whether there's an additional mid-speed bus for infotainment.

## Hardware notes

- SW-CAN needs a special transceiver (NCV7356 / TH8056). Standard CAN HATs can't see it.
- ESP32 has one CAN controller → one bus per ESP32.
- SW-CAN has a high-voltage wake-up mode; the transceiver's mode pins must be in normal mode to listen to regular traffic.

## Sniffing method

1. Record a baseline (car on, idle, no input) for ~60s.
2. Do one action at a time, saying/noting a timestamp, and record.
3. In SavvyCAN, diff against the baseline to find IDs/bytes that change.
4. Confirm by repeating the action.
5. Log findings in `can-db/messages.csv`.

## Open questions

- [ ] Which messages does the stock radio send, and does anything complain when they stop?
- [ ] How does the Bose amp turn on — wire or CAN? Is volume sent over CAN?
- [ ] How are chimes triggered — does the radio generate them from CAN state?
- [ ] Are steering wheel buttons on SW-CAN directly or via LIN → BCM → SW-CAN?
- [ ] What wakes the radio when the car is unlocked?
