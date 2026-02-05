---
slug: rak7268cv2-rak7289cv2
title: RAK7268CV2/RAK7289CV2
sidebar_label: RAK7268CV2/RAK7289CV2
---

# RAK7268CV2/RAK7289CV2

This guide covers the setup and configuration of RAK7268CV2 and RAK7289CV2 LoRaWAN gateways for use with The Things Stack (TTS) and ChirpStack.

## Accessing the Gateway

You must first connect to the gateway's local Web UI using one of two methods:

### WiFi AP Mode (Default)

1. Connect your PC to the SSID: `RAK7268CV2_XXXX` or `RAK7289CV2_XXXX` (No password required)
2. Open a browser and navigate to `192.168.230.1`

### Ethernet Mode

1. Connect the gateway's ETH port to your PC
2. Set your PC to a static IP (e.g., `169.254.15.100`) to match the gateway's fallback IP (e.g., `169.254.15.1`)

## Setting the Mandatory Password

When you first access the gateway, you are required to set a password for the root user. It must meet these strict criteria:

- At least 12 characters long
- Includes at least one special character, one number, and one Latin letter

Once set, you will be redirected to the Dashboard, where you will define your country and region. **Copy the 16-character Gateway EUI** displayed there.

## Internet Connectivity

Before the gateway can communicate with TTS or ChirpStack, it needs an uplink under **Network > WAN**:

### Ethernet

Plug the ETH port into your router; it uses DHCP by default.

### WiFi

1. Go to **Wi-Fi**
2. Enable the interface
3. Scan for your local network

### Cellular (LTE Models)

If using a SIM, configure the APN under **Cellular**.

:::info
If not using a SIM, disable this interface to prevent `SIM_ABSENT` log spam.
:::

## Registration on The Things Stack (TTS)

1. Log in to your TTS Console (e.g., `hardwario-com.eu1.cloud.thethings.industries`)
2. Go to **Gateways** > **+ Register gateway**
3. Paste your Gateway EUI and select the correct Frequency Plan (e.g., Europe 863-870 MHz)
4. Navigate to **API Keys** > **+ Add API key**
5. Select "Link as Gateway to a Gateway Server..." and click **Create API key**
6. Copy the key string (e.g., `NNSXS...`) immediately

## Registration on ChirpStack (v4)

1. Log in to your ChirpStack Console (e.g., `http://your-ip-address:8080`)
2. Go to **Gateways** > **+ Add gateway**
3. Paste your Gateway EUI (found in your RAK dashboard) into the **Gateway ID (EUI64)** field
4. Select a **Gateway Profile** (e.g., EU868 or US915) that matches your regional plan
5. Navigate to **API Keys** (found under the Tenant or System menu in the sidebar)
6. Click **+ Create API key**, give it a name like "RAK7268-BasicsStation", and click **Submit**
7. Copy the API Key string immediately; you will use this in the "Gateway Token" field on your RAK7268 if you choose to use Token-based authentication

## Configuring Work Modes

Navigate to **LoRa > Configuration** and select **Basics™ Station** to connect to TTS:

### Basics Station Configuration

- **Basics Station Mode**: LNS Server
- **Server URL**: `wss://hardwario-com.eu1.cloud.thethings.industries` (Port 8887)
- **Trust (CA Certificate)**: Upload the [ISRG Root X1 .pem file](https://letsencrypt.org/certs/isrgrootx1.pem)
- **Client Token**: Paste your TTS API Key

### Other Available Work Modes

- **Packet Forwarder**: Used for legacy Semtech UDP or ChirpStack MQTT connections
- **Built-in Network Server**: Allows the gateway to act as its own standalone LNS (ChirpStack)