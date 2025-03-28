# iBeacon Project

## Overview
This project configures an ESP32-WROOM-DA module as an iBeacon, broadcasting a Bluetooth Low Energy (BLE) signal with a predefined UUID, Major, Minor, and TX Power. It also uses an ST7735 TFT display to show a startup splash screen (karma bitmap) and real-time beacon data. The project is designed for the "HackIt" initiative, demonstrating BLE advertising capabilities.

## Authors
- Patrick Verheul
- Grok (xAI)

## Date / Version
- March 17, 2025 - v1.0

## Repository
- GitHub: https://github.com/patrickverheul/iBeacon-Project

## Hardware Requirements
- **ESP32-WROOM-DA Module**: Main microcontroller with BLE support.
- **ST7735 TFT Display**: 1.8" color display (128x160 resolution) with SPI interface.
- **Wiring**:
  - TFT_CS: GPIO 15
  - TFT_RST: GPIO 4
  - TFT_DC: GPIO 21
  - TFT_MOSI: GPIO 23
  - TFT_SCLK: GPIO 18

## Software Requirements
- **Arduino IDE**: Programmed with the ESP32 board support package.
- **Libraries**:
  - `Adafruit_GFX` (core graphics library)
  - `Adafruit_ST7735` (TFT hardware library)
  - `SPI` (included with Arduino IDE)
  - `ESP32 BLE Arduino` (for BLE functionality)
- **karma.h**: Custom header file containing a 128x168 RGB bitmap array (must be generated separately).

## Setup Instructions
1. **Install Libraries**:
   - Install the required libraries via the Arduino Library Manager.
2. **Prepare karma.h**:
   - Convert a 128x168 image to a C array using a tool like LCD Image Converter.
   - Save as `karma.h` in the `src/` directory.
3. **Configure Arduino IDE**:
   - Board: ESP32-WROOM-DA Module
   - Upload Speed: 115200
   - CPU Frequency: 240 MHz (WiFi/BT)
   - Flash Frequency: 80 MHz
   - Flash Mode: QIO
   - Flash Size: 4MB (32Mb)
   - Partition Scheme: Default 4MB with spiffs (1.2MB APP/1.5MB SPIFFS)
   - Port: (e.g., COM26, adjust as needed)
4. **Upload Code**:
   - Connect the ESP32 to your computer.
   - Open `src/iBeacon.ino` in Arduino IDE and upload it.

## Functionality
- **Startup**:
  - Displays a "karma" bitmap for 2 seconds.
  - Shows "HackIt Beacon" in yellow text for 5 seconds.
- **iBeacon**:
  - Broadcasts an iBeacon signal with:
    - UUID: `2f234454-cf6d-4a0f-adf2-f4911ba9ffa6`
    - Major: 1
    - Minor: 42
    - TX Power: -56 dBm
- **TFT Display**:
  - Updates to show beacon status and raw data in hex format.
- **Serial Output**:
  - Prints debug messages, UUID, Major, Minor, Power, and raw beacon data.

## Output Example
