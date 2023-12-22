---
title: Device Optimization Overview
author: TerryWarwick
ms.author: twarwick
ms.date: 12/22/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise Device Optimization Overview
keywords: IoT Enterprise, Overview, Optimization
---

# Device Optimization Overview

Windows IoT Enterprise is configured to run with 2GB RAM and 16GB flash configurations on the [LTSC SKU](/windows/iot/iot-enterprise/commercialization/licensing#long-term-servicing-channel-ltsc) only. For other editions of Windows IoT Enterprise, please review and follow the appropriate [hardware requirements](/windows/iot/iot-enterprise/hardware/hardware_requirements).

## Building an Optimized Device

Windows IoT devices are considered [fixed purpose](/windows/iot/iot-enterprise/commercialization/licensing#fixed-purpose-devices) and OEMs are responsible for the configuration and validation of their devices.

OEMs must consider their device scenarios and plan ahead if they choose to use mechanisms like standard [Windows Update](/windows/iot/iot-enterprise/device-management/device-management-overview#update-management) versus [alternative image reflash mechanisms](/windows/iot/iot-enterprise/device-management/reset-and-recovery) and/or other service components that may periodically expect more memory than your base configuration, such as [Azure IoT Edge for Linux on Windows](/windows/iot/iot-enterprise/azure-iot-edge-for-linux-on-windows).

OEMs must also plan to have potential minor expansions of the LTSC working-set and storage requirements due to security patching.

We recommend reviewing our [minimum hardware guidance](/windows/iot/iot-enterprise/hardware/hardware_requirements), features to assist with [reducing disk footprint](reduce-disk-footprint.md) and guidance for [disabling system services](services.md) to optimize device storage and RAM usage.

<!-- For CompactOS See https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/compact-os?view=windows-11 -->

<!-- For Component Store See https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/manage-the-component-store?view=windows-11 -->

## Storage Optimization

| Feature            | Description |
|--------------------|-------------|
| **Removable Packages** | |
| **Optional Features**  | |
| **Features on Demand** | |
| **Drivers**            | |
| **Language packs**     | |
| **Applications**       | |
| **Reserved Storage**   | |
| **Hibernation**        | |
| **Page File**          | |
| **Compact OS**         | + Additional compression|
| **Single-instancing**  | |
| **Component Store**    | |

## Memory Optimization

| Feature            | Description |
|--------------------|-------------|
| **Services**           | |
| **Page File**          | |
