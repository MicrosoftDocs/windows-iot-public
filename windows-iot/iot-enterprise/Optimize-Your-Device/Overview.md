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
Windows IoT Enterprise is configured to run with 2GB RAM and 16GB flash configurations on the [LTSC SKU](/windows/iot/iot-enterprise/commercialization/licensing#long-term-servicing-channel-ltsc) only.

## Building an Optimized Device
Since Windows IoT devices are considered [fixed purpose](/windows/iot/iot-enterprise/commercialization/licensing#fixed-purpose-devices) and the OEM is responsible for the configuration and validation, it is important to validate your configuration carefully and consider if you plan to use mechanisms like standard [Windows Update](/windows/iot/iot-enterprise/device-management/device-management-overview#update-management) versus [alternative image reflash mechanisms](/windows/iot/iot-enterprise/device-management/reset-and-recovery) and/or other service components that may periodically expect more memory than your base configuration, such as [Azure EFLOW](/windows/iot/iot-enterprise/azure-iot-edge-for-linux-on-windows). You must also plan to have potential minor expansions of the LTSC working-set and storage requirements due to security patching.

We recommend reviewing our [Hardware Requirements](/windows/iot/iot-enterprise/hardware-guidance/hardware_requirements), features to assist with [Reducing Disk Footprint](/windows/iot/iot-enterprise/optimize-your-device/removable-packages) and [Disabling System Services Guidance](/windows/iot/iot-enterprise/optimize-your-device/services?branch=pr-en-us-8) to optimize your devices storage and ram usage. 
