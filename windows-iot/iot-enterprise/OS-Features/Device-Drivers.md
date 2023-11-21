---
title: Device Drivers
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about what Technical Components of Windows IoT Enterprise.
keywords: IoT Enterprise, Device Drivers
---

# Device Drivers

Device Drivers are essential for any IoT device. This section outlines how to write device drivers, how driver signing works in Windows IoT Enterprise (different than traditional client signing), and how to add device drivers to images.  

## How to Write Device Drivers

Windows contains [built-in drivers](/windows-hardware/drivers/gettingstarted/do-you-need-to-write-a-driver-) for many device types. If there's a built-in driver for your device type, you don't need to write your own driver. Your device can use the built-in driver. However if you need to write a device driver for your device, use the programming reference for [Windows Driver Kit (WDK)](/windows-hardware/drivers/ddi/).  

## Device Signing

With Windows IoT Enterprise, you have two options on how to get your driver signed off by Microsoft. The first is the [traditional client signing](/windows-hardware/drivers/install/driver-signing ) process and the second is [attestation signing](/windows-hardware/drivers/dashboard/attestation-signing-a-kernel-driver-for-public-release).

### Traditional Client Signing

For typical traditional client signing, if you're unfamiliar with the device and driver installation process, we recommend that you start by reviewing [Roadmap for Device and Driver Installation](/windows-hardware/drivers/install/roadmap-for-device-and-driver-installation--windows-vista-and-later-). You may also want to read [Overview of Device and Driver Installation](/windows-hardware/drivers/install/overview-of-device-and-driver-installation) for a high-level overview of this process and its components.

### Attestation Signing

Follow this article to learn how [attestation signing](/windows-hardware/drivers/dashboard/attestation-signing-a-kernel-driver-for-public-release) works for a kernel driver for public release.

> [!NOTE]
> When a driver receives attestation signing, it is not Windows Certified. An attestation signature from Microsoft indicates that the driver can be trusted by Windows, but because the driver has not been tested in HLK Studio, there are no assurances made around compatibility, functionality, etc.

## How to Add Device Drivers to Images

With Windows IoT Enterprise, you can add device drivers to a Windows image before, during, or after you deploy the image. When planning how to add drivers to your Windows deployment, it's important to understand how driver folders are added to the image, how driver ranking affects deployment, and the digital signature requirements for drivers. To understand more about how to add drivers, check out the following article, [Device Drivers](/windows-hardware/manufacture/desktop/device-drivers-and-deployment-overview).

## Supported Arm 64 Drivers

|Type  |Driver  |Vendor  |Platform  |Notes |
|---------|---------|---------|---------|--------|
|Display  |HDMI |NXP|i.MX 8 family, i.MX 93  |Included in NXP BSP   |
|Display  |MIPI-DSI  | NXP  |i.MX 8 family, i.MX 93 |Included in NXP BSP|
|Display  |LVDS |NXP     |i.MX 8 family, i.MX 93  |Included in NXP BSP|
|Connectivity|Ethernet MAC (internal to SoC)|NXP |i.MX 8 family, i.MX 93|Included in NXP BSP|
|Connectivity|Ethernet PHY AR8031|Qualcomm|i.MX 8 family (except for i.MX 8M Plus)|Included in NXP BSP|
|Connectivity|Ethernet PHY RTL8211FDI|Realtek|i.MX 8M Plus, i.MX 93|Included in NXP BSP|
|Connectivity|WiFi 5 88W8897|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Connectivity|WiFi 5 88W8997|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|GPIO (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|I2C (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|SPI (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|UART (internal to SoC)|NXP|i.MX 8 family (except i.MX 8X)|Included in NXP BSP|
|Low Powered Bus|LPUART (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|Low Powered Bus|CAN Bus (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|USB|USB2 Controller (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in Windows|
|USB|USB3 Controller (internal to SoC)|NXP|i.MX 8 family|Included in Windows|
|USB|USB-C Power Delivery (internal to SoC)|NXP|i.MX 8 family, i.MX 93|Included in NXP BSP|
|USB|USB HID|Any|Any|Included in Windows|
|USB|USB Audio|Any|Any|Included in Windows|
|USB|USB Modems (serial-based CDC devices)|Any|Any|Included in Windows, Arm 64 modem calibration driver not available|
|USB|USB Mass Storage (e.g. thumb drive, SD card reader)|Any|Any|Included in Windows|
|USB|USB Hub|Any|Any|Included in Windows|
|USB|USB Smart Card|Any|Any|Included in Windows|
|USB|USB Printer|Any|Any|Included in Windows|
|USB|USB Scanner|Any|Any|Included in Windows|
|USB|USB Digital Camera|Any|Any|Included in Windows|
|USB|USB Cameras/Webcam|Any|Any|Included in Windows|
|USB|USB Bluetooth Adapter|Any|Any|Included in Windows|
|Camera|MIPI-CSI Camera OV5640|NXP|i.MX 8 family, i.MX 93|Included in BSP|
|Camera|MIPI-CSI Camera OV10635|NXP|i.MX 8 family, i.MX 93|Included in BSP|
|Sensors|Accelerometer/Magnetometer (I2C) FXOS8700|NXP|i.MX 8X|Included in BSP|
|Sensors|Pressure(I2C) MPL3115A2|NXP|i.MX 8X|Included in BSP|
|Sensors|Ambient light (I2C) ISL29023IROZ-T7|NXP|i.MX 8X|Included in BSP|
|Sensors|Gyroscope (I2C) FXAS21002CQ|NXP|i.MX 8X|Included in BSP|
|PWM|PWM|NXP|i.MX8 family, i.MX 93|Included in BSP|