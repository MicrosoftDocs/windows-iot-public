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

## Storage Optimization

| Feature            | Description |
|--------------------|-------------|
| **Features on Demand** | Features on Demand (FODs) are Windows features that can be added at any time, such as [language packs](/windows-hardware/manufacture/desktop/features-on-demand-language-fod), network drivers, networking tools and wireless display. For more information, see [Features On Demand Overview](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities) and [Available Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod). |
| **Languages**  | Many display languages and language features are also delivered as Features on Demand. You can save disk space by choosing not to include some language components in your image. For more information, see [Language Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-language-fod)|
| **Legacy Optional Features** | Prior to the introduction of Features on Demand, Optional Features were offered through Control Panel - Turn Windows Features On or Off and many are still managed in this way.  For more information, see [Enable or Disable Windows Features using DISM](/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism). |
| **Removable Packages** | In addition to Features on Demand and Legacy Optinal Components, Windows IoT Enterprise LTSC supports the removal of additional packages. For more informaion, see [Removable Packages Overview](Removable-Packages.md). |
| **Drivers** | Remove unnecessary drivers.  For more information, see [Add and Remove Driver packages to an offline Windows Image](/windows-hardware/manufacture/desktop/add-and-remove-drivers-to-an-offline-windows-image).  |
| **Applications**       | Software applications that are installed on the computer may require additional space for caches, logs, and updates. Disk space must also be available on the drive to account for temporary increases in resource usage during installation of applications, patches, and updates. |
| **Reserved Storage**   | Windows reserves a portion of storage space on your device for use by temporary files, caches, and other files. When your device is low on space, Windows will clear reserved storage so it can be used for other processes, like a Windows update.. For more information, see [Reserved Storage Command-line Options](/windows-hardware/manufacture/desktop/dism-storage-reserve). |
| **Hibernation**        | Hibernation was designed for mobile computers and might not be available for all PCs. Hibernation leverages a hibernation file to provide a fast startup experience. For more information, see [System Power States - Hibernate State: S4](/windows/win32/power/system-power-states) and [How to enable or disable hibernation](/troubleshoot/windows-client/deployment/disable-and-re-enable-hibernation). |
| **Page File**          | Windows designates a section of the hard drive as virtual memory known as the page file, or more specifically, as pagefile.sys. It's used to supplement the computer’s Random Access Memory (RAM) to improve performance for frequently used programs and data. For more information, see [Introduction to page files](/troubleshoot/windows-client/performance/introduction-to-the-page-file), [How to determine the appropriate page file size](/troubleshoot/windows-client/performance/how-to-determine-the-appropriate-page-file-size-for-64-bit-versions-of-windows) and [How can I change the size of a page file?](https://devblogs.microsoft.com/scripting/how-can-i-change-the-size-of-a-page-file/) </br>**Note:** Review [Peak system commit charge](/troubleshoot/windows-client/performance/how-to-determine-the-appropriate-page-file-size-for-64-bit-versions-of-windows) before disabling the pagefile. |
| **Compact OS**         | Compact OS compresses the files for the entire operating system and lets you run it from the compressed files  to save disk space.  For additional information, see [Compact OS](CompactOS.md) and [Compact command-line utility](/windows-server/administration/windows-commands/compact).</br>**Note:** Best to use with solid-state drives to compensate for performance impact. |
| **Single-instancing**  | After DISM captures the non-system files to a compressed provisioning package, DISM adds pointers on the drive to the new compressed provisioning package, and removes the original files. As a result, the files are still visible to the system, but take up less space on the drive. For more information, see [Single-Instancing of provisioning packages](/windows-hardware/manufacture/desktop/compact-os#single-instancing-of-provisioning-packages) and [DISM /Apply-CustomDataImage](/windows-hardware/manufacture/desktop/dism-provisioning-package-command-line-options#apply-customdataimage) </br>**Note:** Best to use with solid-state drives to compensate for performance impact. |
| **Component Store**    | The Windows Component Store is used to support the functions needed for the customization and updating of Windows. Previous versions of some components are kept on the system for a period of time, allowing you to rollback if necessary. For more information, see [Manage the Component Store](/windows-hardware/manufacture/desktop/manage-the-component-store?view=windows-11) and [Clean Up the WinSxS Folder](/windows-hardware/manufacture/desktop/clean-up-the-winsxs-folder). |

## Memory Optimization

| Feature            | Description |
|--------------------|-------------|
| **Services**           | The Windows operating system includes many system services which may be configured to start automatically, start manually or disabled by default. Some services may be deemed not required for specific fixed function devices and as such can be disabled.  For additional information, see [Disabling system services on Windows IoT Enterprise](Services.md). |
| **Page File**          | Windows designates a section of the hard drive as virtual memory known as the page file, or more specifically, as pagefile.sys. It's used to supplement the computer’s Random Access Memory (RAM) to improve performance for frequently used programs and data.  For more information, see [Introduction to page files](/troubleshoot/windows-client/performance/introduction-to-the-page-file), [How to determine the appropriate page file size](/troubleshoot/windows-client/performance/how-to-determine-the-appropriate-page-file-size-for-64-bit-versions-of-windows).
