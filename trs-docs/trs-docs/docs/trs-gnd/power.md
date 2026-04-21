# TRS-GND — Power

## Power Architecture

TRS-GND is powered from the test stand battery via a barrel jack, managed by the onboard battery manager circuit.

```
[Test Stand Battery] ──barrel jack──► [Battery Manager]
                                              │
                                          +8V rail
                                              │
                                      [AP63205WU Buck]
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

- The external **5V Power Supply** feeds alongside the battery manager
- The **Battery Manager** handles barrel jack input and battery charge/discharge control
- Ensure battery is charged before test stand operations
- 3.3V LED (D3) indicates regulated power is present
