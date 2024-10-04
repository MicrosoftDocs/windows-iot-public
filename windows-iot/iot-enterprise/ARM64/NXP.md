---
title: NXP Overview
author: anch-msft
ms.author: anthonychen
ms.date: 10/2/2024
ms.topic: overview
ms.service: windows-iot
ms.subservice: iot
description: Windows IoT Enterprise on NXP
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

# Windows IoT Enterprise on NXP

Microsoft has worked alongside NXP to enable Windows IoT Enterprise support for NXP's i.MX 8 and i.MX 9 series of Arm64 processors. NXP's i.MX processors enable lower power and lower cost Windows IoT Enterprise devices to be built than ever before while maintaining the familiar user interface, device management, and industry-leading OS support that users love.

For the specific NXP processor models supported by each Windows IoT Enterprise OS version, refer to the [Windows IoT Enterprise Processor Lists](../Hardware/Processor_Requirements.md#windows-iot-enterprise-processor-lists).

## NXP Board Support Package

NXP publishes the Board Support Package (BSP) that includes the drivers and firmware needed for the supported NXP i.MX 8 and i.MX 93 evaluation kits (EVKs) to run on Windows IoT Enterprise. The BSP is provided in both source code and binary format.

To download the BSP for the EVKs and their supporting documentation, visit NXP's [Windows IoT Enterprise for i.MX Applications Processors](https://aka.ms/nxpiot) website.

For hardware platforms other than EVKs, contact the hardware manufacturer for the BSP.

## Features Supported

The table below lists the features supported on each of the NXP i.MX EVK boards as of the most recent NXP BSP release (1.5.1). For details, check the [NXP BSP documentation](https://aka.ms/nxpiot).

| Feature | i.MX 8M Plus | i.MX 8M | i.MX 8M Mini | i.MX 8M Nano | i.MX 8X | i.MX 93 |
|---|-|-|-|-|-|-|
|**Audio**|
| 3.5mm audio jack | input and output | output only | output only | output only | input and output | input and output |
| HDMI audio (output only) | &check; | - | - | - | - | - |
|**Display/Graphics**|
| HDMI | up to 1080p | up to 1080p | - | - | - | - |
| LVDS | up to 1920x1200 | - | - | - | up to 1080p | up to 1280x800 |
| MIPI-DSI | up to 1920x1200 | - | up to 1920x1200 | up to 1920x1200 | - | up to 1920x1200 |
| GPU | &check;| &check; | - | &check; | &check; | - |
| Multiple Displays | &check; | - | - | - | &check; | - |
| VPU video decode (HEVC, H.264, VP8) | &check; | &check; | &check; | - | &check; | - |
| VPU video decode (MPEG-2, MPEG-4) | - | &check; | - | - | &check; | - |
| VPU video decode (VP9) | - | &check; | - | - | - | - |
|**Device Connectivity**|
| USB | &check; | &check; | &check; | &check; | &check; | &check; |
| GPIO | &check; | &check; | &check; | &check; | &check; | &check; |
| UART (RS-232) | &check; | &check; | &check; | &check; | - | - |
| LPUART (RS-232) | - | - | - | - | &check; | &check; |
| I2C (controller mode) | &check; | &check; | &check; | &check; | - | - |
| LPI2C (controller mode) | - | - | - | - | &check; | &check; |
| SPI (controller mode) | &check; | &check; | &check; | &check; | - | - |
| LPSPI (controller mode) | - | - | - | - | &check; | &check; |
| PCIe | &check; | &check; | &check; | - | &check; | - |
| FlexCAN | &check; | - | - | - | &check; | &check; |
|**Network Connectivity**|
| Ethernet | 2x RTL8211 | 1x AR8031 | 1x AR8031 | 1x AR8031 | 1x AR8031 | 2x RTL8211 |
| Wi-Fi 5 <sup>1</sup> | &check; | &check; | &check; | - | &check; | - |
|**Storage**|
| eMMC | &check; | &check; | &check; | &check; | &check; | &check; |
| SD | &check; | &check; | &check; | &check; | &check; | &check; |
|**Camera**|
| OV5640 MIPI-CSI camera ([MINISASTOCSI](https://www.nxp.com/part/MINISASTOCSI)) | &check; | &check; | &check; | &check; | &check; | - |
| OV10635 MIPI-CSI camera ([MX8XMIPI4CAM2](https://www.nxp.com/part/MX8XMIPI4CAM2)) | &check; | &check; | &check; | &check; | &check; | - |
| AP1302 ISP + AR0144 MIPI-CSI camera ([RPI-CAM-MIPI](https://www.nxp.com/part/RPI-CAM-MIPI)) | - | - | - | - | - | &check; |
|**Security**|
| Secure Boot | &check; | &check; | &check; | &check; | &check; | &check; |
|**Miscellaneous**|
| RTC (on-SoC)<sup>2</sup> | &check; | &check; | &check; | &check; | - | - |

<sup>1</sup> Wi-Fi support is added through a PCIe M.2 expansion port. NXP i.MX 8M Plus EVK ships with a supported 88W8997-based M.2 module. NXP provides drivers for M.2 modules based on the 88W8997 and 88W8897 Wi-Fi chips.

<sup>2</sup> Real time clock (RTC) is implemented on-SoC and preserves time across reset, but doesn't preserve time when the system is powered off. Add a discrete RTC to preserve time when the system is powered off.

## Known Limitations

### Windows Forms application performance

Windows Forms applications run slower when the GPU is enabled due to how Windows Forms’ underlying graphics API (GDI+) handles rendering. You can prevent this performance slowdown by disabling the GPU for the specific application through registry:

For example, if you want to disable the GPU for an application named WinFormsApp.exe, you can create the following registry key in a command prompt:

```Command Prompt
reg add HKLM\Software\VSI\GPU\GdiRedirSurf /v WinFormsApp.exe /t REG_DWORD /d 0
```

### Browser GPU acceleration

The NXP GPU driver doesn't support acceleration of browser-based workloads. Browser content renders using CPU instead.

### eMMC HS400

Windows IoT Enterprise doesn't support eMMC HS400, which can result in lower peak storage throughput. In addition, the i.MX 93 storage driver doesn't support eMMC HS200.

### Minimum supported Windows 10 IoT Enterprise version: 19044.3693 (KB5032189)

Windows 10 IoT Enterprise must be updated to version 19044.3693 [(KB5032189)](https://support.microsoft.com/en-us/topic/november-14-2023-kb5032189-os-builds-19044-3693-and-19045-3693-fe81e7e5-06bd-4e13-8233-4f7c07b1c512) or newer. Older versions of Windows 10 IoT Enterprise limit the maximum memory on the NXP i.MX 8M Plus to 3GB, and have storage stability issues that can lead to blue screens. To update the Windows IoT Enterprise image offline, follow the [instructions for adding updates to a Windows image](/windows-hardware/manufacture/desktop/servicing-the-image-with-windows-updates-sxs).

### Hyper-V

The i.MX 8 family of application processors don't support Hyper-V virtualization or features that depend on it (for example, Virtualization Based Security).

### NPU

Windows IoT Enterprise doesn't support the NPUs on either the i.MX 8M Plus or the i.MX 93 applications processors.

### PCIe storage

Windows IoT Enterprise doesn't support expandable storage through PCIe (for example, M.2 SSD).

### i.MX 8M 4GB+ memory support

The i.MX 8M applications processor has a hardware limitation that only allows external devices to address the first 3GB of memory (RAM). i.MX 8M systems that have more than 4GB or more memory must ensure their DMA-capable drivers don't address memory outside of the safe 3GB region.

### USB On-The-Go (USB OTG)

Windows IoT Enterprise doesn't support [USB On-The-Go (USB OTG)](https://www.usb.org/usb-on-the-go) and doesn't support USB ports operating in the USB Function role.
