---
title: Supported ARM64 Drivers for NXP i.MX
author: sydbruck
ms.author: sybruckm
ms.date: 12/11/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Supported ARM64 Drivers for NXP i.MX
keywords: IoT Enterprise, Device Drivers
---

# Supported Arm64 Drivers for NXP i.MX Boards

Make full use of Windows IoT Enterprise on your NXP device by selecting devices with existing Arm64 drivers. 

For devices not listed on this page, please work with the device vendor on getting an Arm64 driver built for Windows IoT.

## NXP Supported Drivers

|Type  |Driver  |Vendor  |Platform  |Notes |
|---------|---------|---------|---------|--------|
|Display  |HDMI |NXP|i.MX 8 family, i.MX 93  |Included in NXP BSP. Platforms that do not have HDMI output can use the NXP MIPI converter (IMX-MIPI-HDMI) or LVDS converter (IMX-LVDS-HDMI) |
|Display  |MIPI-DSI  | NXP  |i.MX 8 family (except i.MX 8M Quad, i.MX 8X), i.MX 93 |Included in NXP BSP|
|Display  |LVDS |NXP     |i.MX 8M Plus, i.MX 8X, i.MX 93  |Included in NXP BSP|
|Connectivity|Ethernet MAC (internal to SoC)|NXP |i.MX 8 family, i.MX 93|Included in NXP BSP|
|Connectivity|Ethernet PHY AR8031|Qualcomm|i.MX 8 family (except i.MX 8M Plus) |Included in NXP BSP|
|Connectivity|Ethernet PHY RTL8211FDI|Realtek|i.MX 8M Plus, i.MX 93|Included in NXP BSP|
|Connectivity|WiFi 5 88W8897|NXP|i.MX 8 family, i.MX 8X, i.MX 93|Included in NXP BSP. Tested with AzureWave AW-CB178NF|
|Connectivity|WiFi 5 88W8997|NXP|i.MX 8 family, i.MX 8X, i.MX 93|Included in NXP BSP. Tested with AzureWave AW-CM276NF|
|Low Powered Bus|GPIO (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|I2C (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|SPI (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|UART (internal to SoC)|NXP|i.MX 8 family (except i.MX 8X)|Included in NXP BSP|
|Low Powered Bus|LPUART (internal to SoC)|NXP|i.MX 8X, i.MX 93|Included in NXP BSP|
|Low Powered Bus|CAN Bus (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|USB|USB2 Controller (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in Windows|
|USB|USB3 Controller (internal to SoC)|NXP|i.MX 8 family (except i.MX 8M Mini, i.MX 8M Nano)|Included in Windows|
|USB|USB-C Power Delivery (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|USB|USB HID|Any|Any|Included in Windows|
|USB|USB Audio|Any|Any|Included in Windows|
|USB|USB Modems (serial-based CDC devices)|Any|Any|Included in Windows, Arm64 modem calibration driver not available|
|USB|USB Mass Storage (e.g. thumb drive, SD card reader)|Any|Any|Included in Windows|
|USB|USB Hub|Any|Any|Included in Windows|
|USB|USB Smart Card|Any|Any|Included in Windows|
|USB|USB Printer|Any|Any|Included in Windows|
|USB|USB Scanner|Any|Any|Included in Windows|
|USB|USB Digital Camera|Any|Any|Included in Windows|
|USB|USB Cameras/Webcam|Any|Any|Included in Windows|
|USB|USB Bluetooth Adapter|Any|Any|Included in Windows|
|Camera|MIPI-CSI Camera OV5640|Omnivision|i.MX 8 family, i.MX 93|Included in NXP BSP. Tested with NXP MINISASTOCSI|
|Camera|MIPI-CSI Camera OV10635|Omnivision|i.MX 8 family, i.MX 93|Included in NXP BSP. Tested with NXP MX8XMIPI4CAM2|
|Sensors|Accelerometer/Magnetometer (I2C) FXOS8700|NXP|i.MX 8X|Included in NXP BSP|
|Sensors|Pressure(I2C) MPL3115A2|NXP|i.MX 8X|Included in NXP BSP|
|Sensors|Ambient light (I2C) ISL29023IROZ-T7|Renesas|i.MX 8X|Included in NXP BSP|
|Sensors|Gyroscope (I2C) FXAS21002CQ|NXP|i.MX 8X|Included in NXP BSP|
|PWM|PWM (internal to SoC)|NXP|i.MX8 family, i.MX 93|Included in NXP BSP|
