---
title: Device Optimization Overview
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise Device Optimization Overview
keywords: IoT Enterprise, Overview, Optimization
---

# Device Optimization Overview

Windows IoT Enterprise is configured to run with 2GB RAM and 16GB flash configurations on the [LTSC SKU](/windows/iot/iot-enterprise/commercialization/licensing#long-term-servicing-channel-ltsc) only. For other editions of Windows IoT Enterprise, please review and follow the appropriate [hardware requirements](/windows/iot/iot-enterprise/hardware/hardware_requirements).

## Building an Optimized Device

Windows IoT devices are considered [fixed purpose](/windows/iot/iot-enterprise/commercialization/licensing#fixed-purpose-devices) and OEMs are responsible for the configuration and validation of their devices. OEMs must consider their device scenarios and plan ahead if they choose to use mechanisms like standard [Windows Update](/windows/iot/iot-enterprise/device-management/device-management-overview#update-management) versus [alternative image reflash mechanisms](/windows/iot/iot-enterprise/device-management/reset-and-recovery) and/or other service components that may periodically expect more memory than your base configuration, such as [Azure IoT Edge for Linux on Windows](/windows/iot/iot-enterprise/azure-iot-edge-for-linux-on-windows). OEMs must also plan to have potential minor expansions of the LTSC working-set and storage requirements due to security patching.

> [!TIP]
>
> A device running the Windows 10 IoT Enterprise LTSC 2021 OS on the minimum hardware, 2 GB of RAM and 16 GB of storage, has been configured in one sample exercise to utilize 300MB of RAM and 5.5GB of storage.

We recommend reviewing our [minimum hardware guidance](/windows/iot/iot-enterprise/hardware/hardware_requirements), features to assist with [reducing disk footprint](/windows/iot/iot-enterprise/optimize/removable-packages) and guidance for [disabling system services](/windows/iot/iot-enterprise/optimize/services) to optimize device storage and RAM usage.
