---
title: Device Optimization Overview
author: rsameser
ms.author: riameser
ms.date: 5/24/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise Device Optimization Overview
keywords: IoT Enterprise, Overview, Optimization
---

# Device Optimization Overview
Windows IoT Enterprise can be configured to run in 2GB RAM and 16GB flash configurations on the [LTSC SKU](/windows/iot/iot-enterprise/commercialization/licensing#long-term-servicing-channel-ltsc) only. When configured in the [minimum footprint](/windows/iot/iot-enterprise/hardware-guidance/hardware_requirements), an example consumption view on Windows IoT Enterprise could be as small as 300MB of runtime RAM consumption and 5.5 GB of OS flash consumption.

## Building an optimized device
Windows 10 was originally released with a minimum hardware requirement of 1GB RAM and 24GB Flash for 64-bit architectures. Upgrades are supported from this smaller RAM configuration on the original devices.

Since Windows IoT devices are considered [fixed purpose](/windows/iot/iot-enterprise/commercialization/licensing#fixed-purpose-devices) and the OEM is responsible for the configuration and validation, Windows IoT OEMs are able to create devices that are below the [minimum hardware requirements](/windows/iot/iot-enterprise/hardware-guidance/hardware_requirements) on LTSC-only.  

When running on hardware below the minimum specification, it is important to validate your configuration carefully and consider if you plan to use mechanisms like standard [Windows Update](/windows/iot/iot-enterprise/device-management/device-management-overview#update-management) versus [alternative image reflash mechanisms](/windows/iot/iot-enterprise/device-management/reset-and-recovery) and/or other service components that may periodically expect more memory than your base configuration, such as [Azure EFLOW](/windows/iot/iot-enterprise/azure-iot-edge-for-linux-on-windows). You must also plan to potential minor expansions of the LTSC working-set and storage requirements due to security patching.

## Additional Resources
* [Hardware Requirements](/windows/iot/iot-enterprise/hardware-guidance/hardware_requirements)
* [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize-your-device/removable-packages)
* [System Services Guidance](/windows/iot/iot-enterprise/optimize-your-device/services?branch=pr-en-us-8)
