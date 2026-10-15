# Roadmap

Check items off as they're done. Each phase should end with something that works on its own.

## Phase 0 — Sniffer build
- [ ] Order single-wire CAN transceiver breakout (NCV7356 or TH8056)
- [ ] Order male OBD-II pigtail with pins 1, 4, 5, 16 wired
- [ ] Wire ESP32 + transceiver on a breadboard (see `sniffer/README.md`)
- [ ] Flash ESP32RET, configure 33.3 kbps
- [ ] Connect SavvyCAN on laptop, confirm it sees the board

## Phase 1 — Sniff & decode
- [ ] First capture: car on, nothing touched (baseline)
- [ ] Capture each steering wheel button, one at a time
- [ ] Capture climate controls (temp, fan, mode, A/C, recirc)
- [ ] Capture door open/close, seatbelt, key-in, lights (chime triggers)
- [ ] Capture reverse gear (camera trigger)
- [ ] Capture ignition off → on → off (wake/sleep sequence)
- [ ] Identify messages the stock radio *sends* (heartbeat candidates)
- [ ] Record every decoded message in `can-db/messages.csv`
- [ ] Optional: second ESP32 + SN65HVD230 for high-speed CAN (speed, RPM)

## Phase 2 — Research the stock head unit
- [ ] Get SS / VF Commodore wiring diagram for the radio and screen
- [ ] Confirm if the system is one unit or screen + separate receiver
- [ ] Identify connector part numbers, find matching plugs/adapters
- [ ] Measure mic bias voltage at the connector (stock unit running)
- [ ] Determine Bose amp input type (analog vs digital) and turn-on method
- [ ] Determine backup camera video format
- [ ] Fill in `docs/wiring.md` pinout table

## Phase 3 — Bench prototype
- [ ] Pi 5 + display + NVMe running on the bench
- [ ] Pi talks to body bus (MCP2515 + transceiver) via SocketCAN
- [ ] Replay captured logs to the Pi to develop without the car
- [ ] Basic UI: home, media, settings
- [ ] Android Auto working (wired) on bench
- [ ] Audio out through DAC; mic in for calls

## Phase 4 — In-car testing (stock unit stays installable)
- [ ] Automotive power supply with ignition sense + delayed shutdown
- [ ] Steering wheel buttons control the UI
- [ ] Climate status shown on screen
- [ ] Chimes play correctly
- [ ] Bose amp turns on and plays audio
- [ ] Backup camera shows on reverse
- [ ] No warning lights / fault codes with stock unit removed
- [ ] Decide if ESP32 bridge is needed (boot-time heartbeats, wake-on-CAN)

## Phase 5 — Final install
- [ ] Design and print bezel
- [ ] Mount display, route cabling, secure everything
- [ ] Boot-time tuning
- [ ] Wireless Android Auto (stretch)
- [ ] Vehicle settings menus (stretch)
