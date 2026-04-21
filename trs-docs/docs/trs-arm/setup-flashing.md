# TRS-ARM — Setup & Flashing

The flashing procedure for TRS-ARM is identical to TRS-GND. Refer to [TRS-GND Setup & Flashing](../trs-gnd/setup-flashing.md) for SWD and USB DFU instructions.

> **Important:** TRS-ARM must be flashed and verified **before** integration into the airframe.
## TRS-ARM Configuration

| Parameter | Value |
|-----------|-------|
| Role | Rocket radio + FC switch control |
| Radio frequency | 915 MHz |
| FC Switch default state | DISARMED (open) on boot |
| Ethernet | Disabled / not connected |
| UART baud (LoRa module) | _TODO: confirm_ |

## Pre-Integration Checklist

- [ ] Firmware flashed and verified via SWD
- [ ] Radio link confirmed with TRS-GND
- [ ] FC switch tested: ARM command closes switch, DISARM opens it
- [ ] FC switch defaults to **disarmed** state on cold boot
- [ ] 8.4V battery voltage confirmed ≥ 8.0V
- [ ] Antenna connected to J4 (coaxial)
- [ ] USB-C and SWD cables removed before airframe close-out
- [ ] Telemetry packets visible at GSE laptop before integration

## Arming Procedure (Field)

1. Rocket integrated and on launch rail
2. Ground operator sends **ARM** command from GSE laptop
3. TRS-ARM receives command over LoRa and asserts FC switch
4. Easy Mini flight computer powers on and enters armed state
5. Confirm arm state via telemetry feedback to ground

## Disarm / Safe Procedure

1. Ground operator sends **DISARM** command from GSE laptop
2. TRS-ARM de-asserts FC switch — Easy Mini loses power
3. Confirm disarm via telemetry before approaching rocket

## Troubleshooting

| Symptom | Check |
|---------|-------|
| No radio link from bench | Confirm antenna on J4, verify TRS-GND/ECU powered |
| FC switch not responding | Check NMOS gate signals on PC14/PC15, verify optocoupler |
| Board not booting | Check 8.4V battery voltage, verify D3 LED |
| SWD not detected | Confirm NRST not held low, check J3 wiring |
| ARM command not received | Verify LoRa frequency and spreading factor match ground units |
