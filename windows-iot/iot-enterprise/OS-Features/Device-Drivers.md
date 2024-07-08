---
title: Device Drivers
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about what Technical Components of Windows IoT Enterprise.
keywords: IoT Enterprise, Device Drivers
---

# Device Drivers

Device Drivers are essential for any IoT device. This section outlines how to write device drivers, how driver signing works in Windows IoT Enterprise (different than traditional client signing), and how to add device drivers to images.  

## How to Write Device Drivers

Windows contains [built-in drivers](/windows-hardware/drivers/gettingstarted/do-you-need-to-write-a-driver-) for many device types. If there's a built-in driver for your device type, you don't need to write your own drive; your device can use the built-in driver. However if you need to write a device driver for your device, use the programming reference for [Windows Driver Kit (WDK)](/windows-hardware/drivers/ddi/).

## ARM64 Device Drivers

IoT devices with ARM64 processors need drivers that are built specifically for the ARM64 architecture. Many of the same built-in drivers in the X64 version of Windows IoT Enterprise are included in the ARM64 version of Windows IoT Enterprise built for ARM64. Additional ARM64 drivers are provided by the processor vendor or the board vendor in a board's Board Support Packages (BSP). Many device vendors also provide drivers for their devices through either Windows Update or through 3rd-party support channels.

If you need to write an ARM64 device driver for your device, follow the ARM64 driver development documentation on [building ARM64 Drivers with the Windows Driver Kit (WDK)](/windows-hardware/drivers/develop/building-arm64-drivers)

## Kernel Mode Device Driver Signing

Windows IoT Enterprise shares the same [kernel mode driver signing policy as Windows](/windows-hardware/drivers/install/driver-signing), requiring each kernel mode driver to be digitally signed by a trusted source before it can be loaded.

### Test-Signed Drivers

[Test-signed drivers](/windows-hardware/drivers/install/introduction-to-test-signing) are drivers that are digitally signed by a test certificate and are used during driver development and testing. 

In order for a test-signed driver to be loaded, the [TESTSIGNING option must be enabled in the Windows Boot Configuration Database](/windows-hardware/drivers/install/the-testsigning-boot-configuration-option), and the test certificate used to test-sign the driver must be [installed into the certificate store of the system](/windows-hardware/drivers/install/installing-a-test-certificate-on-a-test-computer).

### Production-Signed Drivers

When you're ready to go into production, there are two options on how to get your driver production-signed by Microsoft. The first is the [traditional client signing](/windows-hardware/drivers/install/driver-signing ) process and the second is [attestation signing](/windows-hardware/drivers/dashboard/attestation-signing-a-kernel-driver-for-public-release).


#### Traditional Client Signing

For typical traditional client signing, if you're unfamiliar with the device and driver installation process, we recommend that you start by reviewing [Roadmap for Device and Driver Installation](/windows-hardware/drivers/install/roadmap-for-device-and-driver-installation--windows-vista-and-later-). You may also want to read [Overview of Device and Driver Installation](/windows-hardware/drivers/install/overview-of-device-and-driver-installation) for a high-level overview of this process and its components.

#### Attestation Signing

Follow this article to learn how [attestation signing](/windows-hardware/drivers/dashboard/attestation-signing-a-kernel-driver-for-public-release) works for a kernel driver for public release.

> [!NOTE]
> When a driver receives attestation signing, it is not Windows Certified. An attestation signature from Microsoft indicates that the driver can be trusted by Windows, but because the driver has not been tested in HLK Studio, there are no assurances made around compatibility, functionality, etc. In addition, attestation-signed drivers do not get published on Windows Update.

## How to Add Device Drivers to Images

With Windows IoT Enterprise, you can add device drivers to a Windows image before, during, or after you deploy the image. When planning how to add drivers to your Windows deployment, it's important to understand how driver folders are added to the image, how driver ranking affects deployment, and the digital signature requirements for drivers. To understand more about how to add drivers, check out the following article, [Device Drivers](/windows-hardware/manufacture/desktop/device-drivers-and-deployment-overview).
