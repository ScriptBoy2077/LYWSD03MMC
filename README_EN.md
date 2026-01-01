# Bluetooth Thermometer/Hygrometer Data Collector

## Overview
Cyclically reads temperature and humidity data from **Xiaomi Mijia Bluetooth Thermometer/Hygrometer 2** (LYWSD03MMC) and stores it into an SQLite database file.

> **Important**: The device **must be flashed with a custom firmware** (pvvx ATC_v56.bin) for this script to work properly.

## Prerequisites

### Hardware Requirements
- Xiaomi Mijia Bluetooth Thermometer/Hygrometer 2 (LYWSD03MMC)
- A computer with Bluetooth support

### Firmware Requirements
Must be flashed with custom firmware: **pvvx ATC_v56.bin**

## Firmware Flashing Guide

### 1. Obtain Flashing Tools
- **Firmware & Flashing Tool**: [ATC_MiThermometer](https://github.com/pvvx/ATC_MiThermometer)
- **Device Info Extraction Tool**: [Tokens-Extractor](https://github.com/PiotrMachowski/Xiaomi-cloud-tokens-extractor)

### 2. Browser Settings (Chrome)
1.  Open Chrome browser
2.  Navigate to: `chrome://flags/#enable-experimental-web-platform-features`
3.  Set the option to **Enabled**
4.  Restart the browser

### 3. Obtain Device Parameters
Use the **Tokens-Extractor** tool to obtain the following parameters:
-   `Device known id`
-   `MAC Address`
-   `Mi Token`
-   `Mi Bind Key`

### 4. Flashing Steps
1.  Access the Web interface of `ATC_MiThermometer`
2.  Click the `Connect` button
3.  From the device list, select a Bluetooth device starting with `LYWSD03MMC` (multiple attempts may be needed)
4.  After successful connection, fill in the parameters obtained from `Tokens-Extractor`
5.  Select the firmware: `Custom Firmware: ATC_v56.bin`
6.  Click `Start Flashing` to begin
7.  When `Finished` is prompted and the device name changes to the `ATC_xx` format, the flashing is complete

## Script Usage Instructions

### 1. Install Dependencies
```bash
pip install bleak bthome-ble
```

### 2. Configure Script
Open the `LYWSD03MMC_db.py` file and modify the `DEVICE_MAC` variable on line 23:
```python
DEVICE_MAC = "Your_Device_MAC_Address"  # Replace with the MAC Address obtained from Tokens-Extractor
```

### 3. Run Script
```bash
python LYWSD03MMC_db.py
```
After running, choose option 2 to start reading device data. Continue until the terminal displays "Data saved successfully". 
Note: Ensure the device has Bluetooth enabled and is in a connectable state. Multiple attempts may be required.
