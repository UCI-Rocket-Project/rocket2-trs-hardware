# TRS-ARM — Hardware

## PCB

TRS-ARM uses the shared `rocket2-trs-hardware` PCB. See the [TRS-GND Hardware](../trs-gnd/hardware.md) page for full component table and schematic.

![PCB Schematic](../assets/pcb-schematic.png)

## TRS-ARM Specific Notes

| Item | Detail |
|------|--------|
| Power input | 8.4V LiPo (AV bay battery) |
| Radio count | 1× TRS_RADIO (RFM95W, 915 MHz) |
| FC Switch | **Actively used** — controls Easy Mini arm state |
| Ethernet | Not connected in flight configuration |
| USB-C | Available for pre-flight flashing only |

## FC Switch Circuit

The FC switch is a key feature of TRS-ARM. It uses:

- **TLP3553A** optocouplers (U7, U8) for galvanic isolation
- **NMOS transistors** (NMOS1, NMOS2) gated by STM32 GPIO
- **LOGICA / LOGICB** logic inputs from STM32 via level shifters
- Dual-channel design (channels A and B) for redundancy or staged control

The FC switch gates power or signal to the **Easy Mini flight computer**, controlling when it is armed and able to fire e-matches.

## Enclosure / Mounting

- Mounted inside rocket AV bay
- Antenna routed along airframe for 915 MHz link
- Compact mounting using H1–H4 standoff holes
- No external Ethernet in flight configuration
