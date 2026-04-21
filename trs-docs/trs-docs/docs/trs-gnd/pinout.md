# TRS-GND — Pinout

## STM32F103C8Tx Pin Assignments

| STM32 Pin | Signal | Direction | Description |
|-----------|--------|-----------|-------------|
| PA0 | — | — | ADC / general IO |
| PA2/TX2 | STM_TX_ETH_TX | OUT | UART TX to Ethernet Xport |
| PA3/RX2 | STM_RX_ETH_RX | IN | UART RX from Ethernet Xport |
| PA4 | RADIO_CS | OUT | SPI chip select for RFM95W |
| PA5 | RADIO_SCK | OUT | SPI clock |
| PA6 | RADIO_MISO | IN | SPI MISO |
| PA7 | RADIO_MOSI | OUT | SPI MOSI |
| PA9/TX1 | STM_TX_LORA_TX | OUT | UART TX to LoRa module |
| PA10/RX1 | STM_RX_LORA_RX | IN | UART RX from LoRa module |
| PB0 | ETH_RST | OUT | Ethernet Xport reset |
| PB1 | RADIO_SCK | OUT | Secondary SPI clock |
| PB2 | RADIO_MISO | IN | Secondary MISO |
| PB3 | RADIO_MOSI | OUT | Secondary MOSI |
| PB4 | RADIO_nRST | OUT | Radio reset |
| PB5 | RADIO_CS | OUT | Secondary radio CS |
| PB10/D10 | — | — | General IO |
| PC13 | RADIO_nRST | OUT | RFM95W reset |
| PC14 | NMOS1 | OUT | FC switch NMOS gate 1 |
| PC15 | NMOS2 | OUT | FC switch NMOS gate 2 |
| NRST | NRST | IN | System reset |
| BOOT0 | BOOT0 | IN | Bootloader select |

## External Connectors

| Connector | Pins | Function |
|-----------|------|----------|
| J1 (Conn_01x02_Pin) | 2 | ADC voltage sense input |
| J2 (USB-C) | 16 | USB programming / power detect |
| J3 (ARM Cortex Debug) | VCC, GND, SWDIO, SWCLK, SWO, NRST | SWD debug header |
| J4 (Conn_Coaxial) | ANT | 915 MHz antenna |
| J7 (Screw_Terminal_01x02) | 2 | External signal / power terminal |

## Radio DIO Lines (RFM95W)

| Signal | STM32 Pin |
|--------|-----------|
| RADIO_DIO0 | DIO0 |
| RADIO_DIO1 | DIO1 |
| RADIO_DIO2 | DIO2 |
| RADIO_DIO3 | DIO3 |
| RADIO_DIO4 | DIO4 |
| RADIO_DIO5 | DIO5 |
