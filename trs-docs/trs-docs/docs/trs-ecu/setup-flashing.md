# TRS-ECU — Setup & Flashing

The flashing procedure for TRS-ECU is identical to TRS-GND. Refer to [TRS-GND Setup & Flashing](../trs-gnd/setup-flashing.md) for SWD and USB DFU instructions.

## TRS-ECU Configuration

| Parameter | Value |
|-----------|-------|
| Role | Bunker radio relay |
| Radio frequency | 915 MHz |
| Ethernet IP | Assigned by bunker network switch |
| UART baud (Ethernet Xport) | _TODO: confirm_ |

## Pre-Operation Checklist

- [ ] Firmware flashed and verified
- [ ] 8.4V power supply connected and at correct voltage
- [ ] 3.3V power LED (D3) illuminated
- [ ] Ethernet cable connected to network switch
- [ ] Ethernet link LED active on RJ45
- [ ] Antenna connected to J4 (coaxial)
- [ ] Confirm ECU is reachable from GSE laptop via ping
- [ ] Confirm radio link to TRS-ARM established (check telemetry output)

## Troubleshooting

| Symptom | Check |
|---------|-------|
| No Ethernet link | Check RJ45 cable, verify switch port is active |
| No radio link | Confirm TRS-ARM is powered, check antenna on J4 |
| Not pingable | Check IP config on Ethernet Xport, verify DHCP lease |
| SWD not detected | Check J3 wiring, confirm power is on |
