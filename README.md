# SS Head Unit

A homemade replacement infotainment system for a **2015 Chevy SS** (Holden VF Commodore platform): new screen, Raspberry Pi backend, Android Auto, and full integration with the car's existing CAN-connected systems (steering wheel buttons, climate display, chimes, vehicle settings, Bose amp, backup camera).

## Status

**Phase 0 – Planning & sniffer build.** See [docs/roadmap.md](docs/roadmap.md).

## Repo layout

| Path | What lives there |
|---|---|
| `docs/` | Planning: roadmap, parts list, CAN notes, wiring, decision log |
| `sniffer/` | ESP32 + single-wire CAN sniffer (firmware config, wiring, how to use with SavvyCAN) |
| `can-db/` | Decoded CAN messages: a running message table and, later, a `.dbc` file |
| `logs/` | Raw CAN capture logs from the car (small samples in git; big logs elsewhere) |
| `headunit/` | The head unit software that runs on the Pi |
| `hardware/` | Bezel/enclosure CAD, schematics, power supply notes |

## Architecture (planned)

```
            ┌───────────────── Car ─────────────────┐
            │  Body bus (single-wire CAN, 33.3k)    │
            │  High-speed CAN (500k, read-only)     │
            │  Bose amp · mic · backup camera       │
            └──────┬───────────────┬────────────────┘
                   │ CAN           │ audio / video / mic
         ┌─────────▼────────┐   ┌──▼───────────────────────┐
         │ CAN interface     │   │ DAC · USB capture · mic  │
         │ (MCP2515 + NCV7356│   │ interface                │
         │  or ESP32 bridge) │   └──┬───────────────────────┘
         └─────────┬────────┘      │
                   └──────┬────────┘
                   ┌──────▼──────────────────────┐
                   │ Raspberry Pi 5 (4GB)        │
                   │ Linux · native UI · AA      │
                   └──────┬──────────────────────┘
                          │
                   ┌──────▼──────┐
                   │ 7–8" touch  │
                   └─────────────┘
```

## Safety

- Sniff passively first. Don't transmit on the car's buses until messages are understood.
- Never cut the factory harness — use adapters/pigtails so the stock unit can go back in.
- Fuse everything you connect to 12V.
