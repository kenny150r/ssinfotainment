# Head Unit Software

Runs on the Raspberry Pi 5. Not started yet — this is the plan.

## Planned components

| Component | Job |
|---|---|
| `can/` | SocketCAN reader/writer; turns raw frames into events using `can-db` definitions |
| `ui/` | Touch interface: home, media, climate status, settings, camera |
| `audio/` | Routing to DAC/amp, chimes, mic input |
| `aa/` | Android Auto integration (aasdk-based, or a commercial AA box as a source) |
| `power/` | Ignition sense, safe shutdown, boot-time tuning |
| `tools/` | Log replay to simulate the car on the bench |

## Open choices

- UI toolkit: Qt (QML) vs Flutter vs web kiosk (web needs more RAM)
- Language for CAN/service layer: Python (fast to iterate) vs C++/Rust
- Android Auto approach: aasdk/OpenAuto fork vs commercial AA adapter box
