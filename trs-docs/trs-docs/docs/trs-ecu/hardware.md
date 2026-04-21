# TRS-ECU — Hardware

## PCB

TRS-ECU uses the shared `rocket2-trs-hardware` PCB. See the [TRS-GND Hardware](../trs-gnd/hardware.md) page for full component table and schematic — the hardware is identical.

![PCB Schematic](../assets/pcb-schematic.png)

## TRS-ECU Specific Notes

| Item | Detail |
|------|--------|
| Power input | 8.4V LiPo (via barrel jack / battery connector) |
| Radio count | 1× TRS_RADIO (RFM95W) |
| Ethernet | Connected to bunker network switch via RJ45 |
| FC Switch | Not actively used in ECU role (populated but unused) |
| USB-C | Available for flashing / debug |

## Enclosure / Mounting

- Mounted in the bunker enclosure
- Antenna routed externally for line-of-sight to test stand
- RJ45 connects directly to bunker network switch
