# CAN Database

`messages.csv` is the working notebook of decoded messages. Once things stabilize, convert it to a `.dbc` file (`ss.dbc`) so SavvyCAN, cantools and the head unit can all use the same definitions.

## messages.csv columns

| Column | Meaning |
|---|---|
| bus | `swcan` or `hscan` |
| id | Arbitration ID in hex (e.g. `0x1F5`) |
| sender | Module that sends it, if known |
| byte_bit | Where the signal lives (e.g. `B2.b4`, `B0-B1`) |
| signal | What it means (e.g. `SWC volume up`) |
| values | Observed values and meanings |
| period_ms | How often it repeats (blank if event-driven) |
| confidence | `guess` · `likely` · `confirmed` |
| log | Log file where it was observed |
| notes | |
