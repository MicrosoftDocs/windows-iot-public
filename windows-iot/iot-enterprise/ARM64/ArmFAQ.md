---
title: ARM64 FAQ
author: sydbruck
ms.author: sybruckm
ms.date: 10/20/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Windows IoT Enterprise on ARM64 FAQ
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

# Frequently Asked Questions

## Which hardware is supported?

Windows IoT Enterprise supports various peripheral interfaces on ARM64 devices. The following list isn't exhaustive. There are many other peripherals not listed on this page that are compatible with Windows IoT Enterprise. If you are an IHV with a peripheral that supports Windows IoT Enterprise on ARM64 and would like to be added to this list, reach out to winiotinquire@microsoft.com.

### Connectivity

|Type|Manufacturer  |Name|
|-|-|--------|
|WiFi + Bluetooth|NXP |[88W8897](https://www.nxp.com/products/wireless-connectivity/wi-fi-plus-bluetooth-plus-802-15-4/2-4-5-ghz-dual-band-2x2-wi-fi-5-802-11ac-plus-bluetooth-5-0-solution:88W8897)|
|WiFi + Bluetooth|NXP |[88W8997](https://www.nxp.com/products/wireless-connectivity/wi-fi-plus-bluetooth-plus-802-15-4/2-4-5-ghz-dual-band-2x2-wi-fi-5-802-11ac-plus-bluetooth-5-3-solution:88W8997)|


## Where can I download Windows?

[!INCLUDE [Latest LTSC](../../includes/incl-latest-ltsc-release.md)]

## Which Windows IoT Enterprise version should I use?

Both LTSC and GAC editions of Windows IoT Enterprise are available for NXP devices. You can find more information in our [Processor Requirements](../Hardware/Processor_Requirements.md) page.

|SoC  |Windows 10 IoT Enterprise  |Windows 11 IoT Enterprise  |
|---------|---------|---------|
|i.MX 8M      |    build 19044 or later     |    Not Supported    |
|i.MX 8M Mini |    build 19044 or later     |    Not Supported    |
|i.MX 8M Nano |    build 19044 or later     |    Not Supported    |
|i.MX 8M Plus |    build 19044 or later     |    Not Supported    |
|i.MX 8X      |    build 19044 or later     |    Not Supported    |
|i.MX 93      |    build 19044 or later     |    build 26100.1 or later      |

## Can I run applications that aren't native to ARM64?

On ARM64 devices, Windows IoT Enterprise allows you to run x86 applications without re-compiling the application through emulation. In addition, Windows 11 IoT Enterprise supports running AMD64 applications without re-compiling. For more information, see [How x86 emulation works on Arm](/windows/arm/apps-on-arm-x86-emulation).

## Can I use Hyper-V on my ARM64 device?

Hyper-V is only supported on boards that support Windows 11 IoT Enterprise. For more information, see [Which Windows IoT Enterprise version should I use?](#which-windows-iot-enterprise-version-should-i-use).

## Can I use Windows IoT Enterprise on Qualcomm hardware?

Yes, you can see the list of supported Qualcomm processors on the [Windows 11 processor requirements](../Hardware/supported/Win11_LTSC_2024_Qualcomm_Processors.md) page.

## What drivers are supported?

NXP Drivers: [NXP Supported Drivers](../Hardware/supported/NXP_drivers.md)
