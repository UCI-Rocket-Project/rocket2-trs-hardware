# TRS-GND — Power

## Power Architecture

TRS-GND is powered from a 5V port on the Seeed Studio, managed by the onboard battery manager circuit.

```
[Seeed Studio 5V Port] ──► [Battery Manager]
                                   │
                               +5V rail ──► [USB 5V, Ethernet Xport]
                                   │
                           [AMS1117-3.3 LDO]
                                   │
                              +3.3V rail ──► [STM32, RFM95W, LoRa, Logic]
```

## Regulators

| Regulator | Part | Input | Output | Notes |
|-----------|------|-------|--------|-------|
| U1 | AP63205WU | 8V (battery) | 5V | Switching buck, L1=4.7μH, C4=100nF |
| U3 | AMS1117-3.3 | 5V | 3.3V | LDO, C5=10μF, C6=10μF |

## Decoupling Capacitors

| Location | Value | Rail |
|----------|-------|------|
| C1 | 10μF | 8V input |
| C2, C3 | 22μF | 5V output |
| C8, C9 | 4.7μF | 3.3V |
| C10–C13 | 0.1μF | 3.3V |
| C15 | 10μF | RFM95W 3.3V |

## 3.3V Power Select

The board includes a Schottky diode (D1) and PMOS (Q1) based power select between USB 5V and the regulated 5V rail, preventing backfeed when both supplies are present.

## USB Power Detect

`USB_DETECT` signal (connected via R3 20kΩ pull-down and D4 LED) allows the STM32 to detect when USB is connected.

## Power Notes for TRS-GND

- Powered from the **5V port on the Seeed Studio** via the onboard battery manager
- The **Battery Manager** handles charge/discharge control
- Ensure Seeed Studio is powered before test stand operations
- 3.3V LED (D3) indicates regulated power is present