# TRS-ARM — Pinout

TRS-ARM uses the same PCB and base pin assignments as TRS-GND. Refer to the [TRS-GND Pinout](../trs-gnd/pinout.md) for the full STM32 pin table.

## Active Interfaces for TRS-ARM Role

| Interface | Pins | Used |
|-----------|------|------|
| RFM95W SPI Radio | RADIO_CS, RADIO_SCK, RADIO_MISO, RADIO_MOSI, RADIO_nRST | ✅ Yes |
| FC Switch Channel A | LOGICA1, LOGICA2, NMOS1 (PC14) | ✅ Yes |
| FC Switch Channel B | LOGICB1, LOGICB2, NMOS2 (PC15) | ✅ Yes |
| LoRa UART (SEEEDSTUDIOLORAERMINI) | PA9 (TX), PA10 (RX) | ✅ Yes |
| Ethernet UART (GC-XPORT-ENH) | PA2, PA3 | ❌ Not connected in flight |
| ARM Cortex Debug (J3) | SWDIO, SWCLK, NRST | ✅ Pre-flight flashing |
| USB-C (J2) | USB_DP, USB_DM | ✅ Pre-flight only |
| ADC Voltage Sense (J1) | ADC1 | _Optional_ |

## FC Switch Connector

| Signal | Direction | Description |
|--------|-----------|-------------|
| LOGICA1 | OUT (STM32 → switch) | Channel A arm signal |
| LOGICB1 | OUT (STM32 → switch) | Channel B arm signal |
| NMOS1 | OUT | Channel A MOSFET gate |
| NMOS2 | OUT | Channel B MOSFET gate |
| st11, st12, st21, st22 | — | Screw terminal outputs to Easy Mini |

## Antenna

| Connector | Signal | Description |
|-----------|--------|-------------|
| J4 (Coaxial) | ANT | 915 MHz LoRa antenna |
