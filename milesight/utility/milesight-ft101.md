---
slug: milesight-ft101
title: Milesight - FT101
---

import Image from '@theme/IdealImage';

# Milesight Field Tester FT101

Milesight FT101 is a **portable LoRaWAN® network testing device** designed for **signal assessment and optimization**. It features an **octa-core processor running Android 12.0**, supports **all standard LoRaWAN® frequency bands**, and provides **up to 8 hours of continuous operation**. The device is ideal for evaluating network quality, identifying optimal deployment locations, and comprehensive **field testing of LoRaWAN networks**.


---

## Retrieving Device Keys

**Overview**
FT101 is a **standalone Android device** with a **5.72-inch HD touchscreen**. Configuration and testing are performed through the pre-installed **Field Tester App**.

**Initial Setup**
1. Power on the device and open the **Field Tester** application.
2. **If the device is NOT registered**: The Device EUI and Application Key will be visible on the home screen.
3. Navigate to **Settings > LoRaWAN Settings** to record the **Application EUI** (8-bit code, sometimes labeled as Join EUI).
4. **If the device IS registered**: Go to **Settings > Basic Information** to find:
   - **Device EUI** (8-bit code)
   - **Application Key** (16-bit encryption key)

:::info
The **AppEUI** (Join EUI) is fixed: **24E124C0002A0001**

**DevEUI** (Device Extended Unique Identifier) is unique for each device and can be found printed on the device label.
:::

---

## Device Configuration

Before connecting to the network, ensure the local settings are correct.

1. Connect to **Wi-Fi** and enable **Location Services** in Android Settings.
2. Grant location permission to the **Field Tester App** for GPS tracking.
3. In the app, navigate to **LoRaWAN Settings**.
4. **Frequency Plan**: Select **EU868** (standard for Europe/Czech Republic).
5. **Save**: Tap the Save button to apply changes.

**Additional Options**
- Configurable **Tx power**, **reporting interval** (6-60s), and **spreading factor**.
- **Mock sensor mode** to simulate different Milesight devices.
- Test results are stored on **64GB internal storage**, exportable via USB Type-C or microSD.

---

## LNS Registration (Server-Side)

This process occurs within your LoRaWAN Network Server interface (e.g., TTN, ChirpStack, or Milesight IoT Cloud).

### Registration Steps
1. **Create Application**: Create a container (e.g., "Field_Testing").
2. **Add Device**: Enter the **Device EUI** retrieved from the tester.
3. **Connection Settings**: 
   - **Join Mode**: OTAA
   - **LoRaWAN Version**: v1.0.3
   - **Regional Parameters Revision**: RP001 1.0.3
4. **Insert Keys**: Paste the **App EUI** and **App Key**.
5. **Confirmed Data**: Ensure the server is set to respond to confirmed uplinks.

---

## Network Activation (Join)

Monitor the **Network Status** in the top bar of the home screen.

- **Success**: Status changes to **"Connected"**.
- **Troubleshooting**: If it stays "Not connected":
  - Restart the app (close it via the Android task manager).
  - Verify you are within gateway range via LNS logs.
  - Check for typos in the **App Key** (např. záměna '0' a 'O').
  - Ensure the **LoRa antenna** is securely tightened.

---

## Core Functions

| Function | Description | Objective |
|----------|-------------|-----------|
| **Real-time Testing** | Displays instant RSSI and SNR values | Immediate verification of signal |
| **Signal Evaluation** | Tests combinations of DR and SF (SF7–SF12) | Identifying stable settings |
| **Noise Scan** | Scans 863–870 MHz spectrum | Identifying "radio smog" |
| **Coverage Mapping** | GPS-tracked signal quality | Finding optimal deployment spots |



### Interpreting Noise Scan Results
A lower RSSI value (more negative) indicates a cleaner environment.

| RSSI Value | Environment | Recommendation |
|------------|-------------|----------------|
| -110 dBm to -120 dBm | Excellent / Clean | Ideal for gateway installation |
| -90 dBm to -100 dBm | Moderate Interference | Functional, but range may be reduced |
| Higher than -85 dBm | Heavy Interference | Critical. Relocate gateway |

---

## Technical Specifications

### LoRaWAN Configuration
| Parameter | Value |
|-----------|-------|
| LoRaWAN version | 1.0.3 |
| Sensitivity | -137 dBm @ 125kHz, SF=12 |
| Tx Power | 16 dBm (868MHz) / 22 dBm (915MHz) |

### Power Supply & Physical
| Feature | Details |
|---------|---------|
| **Battery** | 4.3V / 4300mAh lithium-ion rechargeable |
| **Storage** | 64GB Internal (up to 256GB microSD) |
| **NFC** | Built-in reader for Milesight ToolBox |
| **Ingress Protection** | IP65 |
| **Approvals** | CE, FCC, RoHS |