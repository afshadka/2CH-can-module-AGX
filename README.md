# AGX 2-Channel CAN Transceiver Board

This repository contains the KiCad schematic, Jetson AGX Orin CAN/GPIO setup, and related files for a dual-channel CAN interface using SN65HVD230 transceivers.


---

## 🧩 Overview

This board is designed to connect two CAN channels from the Jetson AGX Orin to CAN-enabled devices using SN65HVD230 transceivers. It uses a standard 2x20 header compatible with AGX GPIOs and provides both CAN0 and CAN1 support.

---

## 🔌 Hardware Summary

- **Transceivers**: 2x SN65HVD230
- **Connector**: 2x20 GPIO Header
- **Terminating Resistors**: 120Ω
- **Pull-up Resistors**: 10kΩ on R pin
- **LED**: Power indicator (5V)

| Label | Component     | Description              |
|-------|---------------|--------------------------|
| U1/U2 | SN65HVD230    | CAN Transceivers         |
| J1    | 2x20 Header   | GPIO interface to AGX    |
| J2/J3 | Terminal Blocks | CAN_H / CAN_L Output   |
| D1    | LED + Resistor | Power indication        |

---

## 📍 Jetson AGX Orin CAN & GPIO Pin Assignments

| Interface | Signal | Jetson Pin | GPIO Name | Description       |
|-----------|--------|------------|------------|-------------------|
| CAN0      | TX     | Pin 29     | GPIO216    | U1 Pin 1 (D)      |
| CAN0      | RX     | Pin 31     | GPIO218    | U1 Pin 4 (R)      |
| CAN1      | TX     | Pin 33     | GPIO219    | U2 Pin 1 (D)      |
| CAN1      | RX     | Pin 35     | GPIO221    | U2 Pin 4 (R)      |
| +3.3V     | Pin 1/17|            |            | Transceiver Power |
| +5V       | Pin 2/4 |            |            | LED Power         |
| GND       | Pin 6/9/14 |         |            | Common Ground     |

> ⚠️ Pin names may vary slightly based on the carrier board. For custom boards, use the Pinmux tool.

---

## ⚙️ CAN Interface Setup (Jetson AGX Orin)

### Step 1: Enable CAN Interface

Use Jetson-IO (DevKit only):

```bash
sudo /opt/nvidia/jetson-io/jetson-io.py

