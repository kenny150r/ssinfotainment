# Parts List

Prices are rough ballparks from October 2026 planning; check current prices before ordering.

Status: `have` · `ordered` · `need` · `maybe`

## Sniffer (Phase 0)

| Part | Notes | ~Cost | Status |
|---|---|---|---|
| ESP32 dev board (ESP-WROOM-32) | 3-pack on hand; only one needed | — | have |
| Single-wire CAN transceiver breakout | NCV7356 or TH8056. RxD pull-up must go to 3.3V | $5–15 | need |
| Male OBD-II pigtail (J1962M) | Must have pins 1, 4, 5, 16 wired | $8–15 | need |
| Breadboard, jumpers, 4.7k resistor | | $10 | need |
| SN65HVD230 CAN transceiver | Only for high-speed CAN sniffing (2nd ESP32) | $5 | maybe |

Existing Bluetooth OBD reader: only useful if it's an OBDLink MX+ (supports GM single-wire CAN). ELM327 clones can't see the body bus.

## Head unit (Phase 3+)

| Part | Notes | ~Cost | Status |
|---|---|---|---|
| Raspberry Pi 5, 4GB | 8GB not needed for Linux + native UI | $60–90 | need |
| Active cooler | | $5 | need |
| NVMe HAT + small SSD | Faster boot, no SD corruption | $40 | need |
| 7–8" capacitive display | High brightness (800+ nits) for daylight | $70–150 | need |
| MCP2515 CAN module | Pi's CAN controller (SPI), paired with single-wire transceiver | $10–30 | need |
| DAC HAT or USB DAC | Feeds the Bose amp | $30–50 | need |
| Automotive Pi power supply | 12V→5V 5A, ignition sense, delayed shutdown | $30–60 | need |
| USB video capture | Backup camera input | $15–25 | need |
| USB GPS | | $15 | need |
| Mic interface parts | Bias resistor + cap, or USB sound card w/ mic in | $10–15 | need |
| AM/FM tuner (Si4735 or RTL-SDR) | Optional if mostly streaming | $15–40 | maybe |
| Harness adapters / connectors | Match stock head unit plugs | $20–50 | need |
| Fuse tap, wire, heat shrink | | $20 | need |
| Bezel | 3D printed | $10–30 | need |

**Estimated total:** ~$500–750
