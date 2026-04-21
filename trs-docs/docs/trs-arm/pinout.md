# TRS-ARM — Pinout

Same PCB as TRS-GND and TRS-ECU (`rocket2-trs-hardware`). All STM32 pin assignments are identical. The FC switch (NMOS1/NMOS2) is actively used in the ARM role. Ethernet is not connected in flight configuration.

## STM32F103C8Tx Pin Assignments

| Pin No. | STM32 Pin | Signal | Direction | Description | Active in ARM |
|---------|-----------|--------|-----------|-------------|:---:|
| 7 | NRST | NRST | IN | System reset | ✅ |
| 44 | BOOT0 | BOOT0 | IN | Bootloader select (pulled to 3.3V) | ✅ |
| 5 | PD0 | — | — | Crystal OSC (16 MHz Y1) | ✅ |
| 6 | PD1 | — | — | Crystal OSC (16 MHz Y1) | ✅ |
| 2 | PC13 | — | — | General IO | — |
| 3 | PC14 | — | — | General IO | — |
| 4 | PC15 | — | — | General IO | — |
| 18 | PB0 | — | — | General IO | — |
| 19 | PB1 | — | — | General IO | — |
| 20 | PB2 | ETH_RST | OUT | Ethernet Xport reset | ❌ Not connected in flight |
| 39 | PB3 | RADIO_SCK | OUT | SPI clock for RFM95W | ✅ |
| 40 | PB4 | RADIO_MISO | IN | SPI MISO from RFM95W | ✅ |
| 41 | PB5 | RADIO_MOSI | OUT | SPI MOSI to RFM95W | ✅ |
| 42 | PB6 | — | — | General IO | — |
| 43 | PB7 | — | — | General IO | — |
| 45 | PB8 | — | — | General IO | — |
| 46 | PB9 | — | — | General IO | — |
| 21 | PB10 | STM_TX_ETH_RX | OUT | UART TX → Ethernet Xport RX | ❌ Not connected in flight |
| 22 | PB11 | STM_RX_ETH_TX | IN | UART RX ← Ethernet Xport TX | ❌ Not connected in flight |
| 25 | PB12 | RADIO_CS | OUT | SPI chip select for RFM95W | ✅ |
| 26 | PB13 | — | — | General IO | — |
| 27 | PB14 | — | — | General IO | — |
| 28 | PB15 | — | — | General IO | — |
| 10 | PA0 | — | — | General IO | — |
| 11 | PA1 | NRST_LORA | OUT | LoRa module reset | ✅ |
| 12 | PA2 | STM_TX_LORA_RX | OUT | UART TX → LoRa module RX | ✅ |
| 13 | PA3 | STM_RX_LORA_TX | IN | UART RX ← LoRa module TX | ✅ |
| 14 | PA4 | — | — | General IO | — |
| 15 | PA5 | NMOS2 | OUT | FC switch NMOS gate 2 — arms Easy Mini | ✅ |
| 16 | PA6 | NMOS1 | OUT | FC switch NMOS gate 1 — arms Easy Mini | ✅ |
| 17 | PA7 | — | — | General IO | — |
| 29 | PA8 | RADIO_nRST | OUT | RFM95W radio reset | ✅ |
| 30 | PA9 | — | — | General IO | — |
| 31 | PA10 | USB_DETECT | IN | USB connection detect | ✅ |
| 32 | PA11 | USB_DM | I/O | USB D− | ✅ |
| 33 | PA12 | USB_DP | I/O | USB D+ | ✅ |
| 34 | PA13 | SWDIO | I/O | SWD data | ✅ |
| 37 | PA14 | SWCLK | IN | SWD clock | ✅ |
| 38 | PA15 | — | — | General IO | — |

## External Connectors

| Connector | Pins | Function |
|-----------|------|----------|
| J1 (Conn_01x02_Pin) | 2 | +8V input / AV bay LiPo |
| J2 (USB-C) | 16 | USB programming / power detect (pre-flight only) |
| J3 (ARM Cortex Debug) | VCC, GND, SWDIO, SWCLK, SWO, NRST | SWD debug header (pre-flight only) |
| J4 (Conn_Coaxial) | ANT | 915 MHz antenna |
| J7 (Screw_Terminal_01x02) | 2 | FC switch output to Easy Mini |

## Radio DIO Lines (RFM95W U5)

| RFM95W Pin | Signal | Description |
|------------|--------|-------------|
| RST | RADIO_nRST | Active-low reset from STM32 (PA8) |
| CS | RADIO_CS | Active-low SPI chip select from STM32 (PB12) |
| SCK | RADIO_SCK | SPI clock from STM32 (PB3) |
| MOSI | RADIO_MOSI | SPI data in from STM32 (PB5) |
| MISO | RADIO_MISO | SPI data out to STM32 (PB4) |
| ANT | — | Coaxial antenna connector J4 (Conn_Coaxial) |
| DIO0 | RADIO_DIO0 | LoRa interrupt line 0 |
| DIO1 | RADIO_DIO1 | LoRa interrupt line 1 |
| DIO2 | RADIO_DIO2 | LoRa interrupt line 2 |
| DIO3 | RADIO_DIO3 | LoRa interrupt line 3 |
| DIO4 | RADIO_DIO4 | LoRa interrupt line 4 |
| DIO5 | RADIO_DIO5 | LoRa interrupt line 5 |

Power: 3.3V (decoupled by C15 10μF to GND)