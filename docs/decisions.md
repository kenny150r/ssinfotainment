# Decision Log

Newest at the bottom. Record what was decided, why, and what would change it.

## 2026-10-14 — Raspberry Pi 5, 4GB
Linux + native UI + Android Auto fits easily in 4GB. 8GB only matters for full Android, a Chromium UI, or on-device builds.
*Revisit if:* we switch to running Android on the board.

## 2026-10-14 — DIY ESP32 sniffer instead of Macchina M2
M2 is sold out. ESP32 (already on hand) + single-wire CAN transceiver + ESP32RET firmware works with SavvyCAN the same way.

## 2026-10-14 — Pi handles CAN directly (MCP2515 + transceiver); ESP32 bridge optional
Fewer boards, and SocketCAN is easy to work with.
*Revisit if:* the car needs radio heartbeat messages faster than the Pi boots, or we want wake-on-CAN.

## 2026-10-14 — Reuse factory mic and Bose amp
Both should work with the right interface. Fallbacks: clip-on USB mic; aftermarket 4-ch amp.
*Revisit if:* the amp needs a digital input or won't stay on without stock radio messages.

## 2026-10-14 — Never cut the factory harness
Use adapters so the stock unit can always go back in.
